---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Breakdown the overheads of various components of the network stack on
performance - RPC, REST, TCP/IP, QUIC ^hy5uHiyI

We will analyze performance overheads across network stack layers by comparing TCP/IP, REST, RPC/gRPC, and QUIC. Instead of only measuring end-to-end latency, we will identify where time and CPU are spent, including kernel calls, serialization, system calls, and user-space transport logic. We will measure latency, throughput, and CPU overhead using controlled microbenchmarks and profiling tools like perf and strace. We have found some research paper, which are not completely related to our project. We will be using them as reference for our tasks. Additionally, we will include QUIC, as it is the latest transport protocol widely used for video streaming and real-time applications, providing improved performance under packet loss compared to TCP. ^KkdldFzw

Overheads ^17OxVSmO

1. Prepare ubuntu
2. Start measuring overheads one by one for every protocol and learn why that happens
3. Decide what to include what not
4. Decide paper structure
5. Make graphs and charts
6. Make report ^XSPjXHDc

Good — now that the proposal is submitted, the best thing is to follow a **clear execution roadmap** so you don’t wander or waste time. I’ll give you a **complete step-by-step plan** that covers:

* project implementation
* experiments
* measurements
* analysis
* research paper structure
* related work to search for

Think of this as your **project playbook**.

---

# 1. Understand the final research goal

Your project should answer this **core research question**:

> **Where does performance overhead come from in different network communication stacks (TCP/IP, REST, RPC/gRPC, QUIC)?**

Not just:

* which is faster

But:

* **why it is faster/slower**

You will attribute overhead to things like:

* kernel networking
* serialization
* system calls
* transport design
* user-space vs kernel logic

---

# 2. Define the stacks you will test

These are the **four stacks you should benchmark**.

| Stack   | Layers              |
| ------- | ------------------- |
| Raw TCP | TCP                 |
| REST    | HTTP/1.1 + TCP      |
| RPC     | gRPC + HTTP/2 + TCP |
| QUIC    | HTTP/3 + QUIC       |

This lets you observe **incremental overhead**.

---

# 3. Environment setup (Day 1–2)

Use **Linux** (Ubuntu recommended).

Install tools:

```bash
sudo apt update
sudo apt install linux-tools-common linux-tools-generic linux-tools-$(uname -r)
sudo apt install strace tcpdump iproute2
```

Python dependencies:

```bash
pip install flask requests grpcio grpcio-tools aioquic
```

Optional but useful:

```
wrk (HTTP load testing)
FlameGraph tools
```

---

# 4. Implement the baseline services

All protocols should implement **the same operation**:

```
client sends "ping"
server responds "pong"
```

This isolates network overhead.

---

## 4.1 Raw TCP (baseline)

Server:

* socket
* accept
* read
* write

Client:

* send
* receive
* measure round-trip time

Metrics:

* latency
* syscall count
* CPU cycles

---

## 4.2 REST (HTTP/1.1)

Use **Flask**.

Server endpoint:

```
POST /echo
```

Client:

```
requests.post()
```

Payload example:

```json
{"msg":"ping"}
```

Measure:

* JSON serialization
* HTTP header overhead
* TCP cost

---

## 4.3 RPC (gRPC)

Define protobuf:

```
service Echo {
  rpc Ping (Message) returns (Message);
}
```

Measure:

* protobuf serialization
* HTTP/2 framing
* multiplexing

---

## 4.4 QUIC (HTTP/3)

Use **aioquic**.

Measure:

* connection setup latency
* CPU cost
* tail latency under packet loss

---

# 5. Design the experiments

Each protocol should run under **identical conditions**.

Keep these variables fixed:

* payload size
* request rate
* machine
* CPU governor

---

## Experiment 1 — baseline latency

Measure round-trip latency.

Output:

* p50
* p95
* p99

Plot **CDF curves**.

---

## Experiment 2 — throughput

Increase concurrency.

Measure:

```
requests/sec
```

---

## Experiment 3 — CPU overhead

Use:

```bash
perf stat
```

Example:

```
perf stat -e cycles,instructions,cs,syscalls ./client
```

Collect:

* cycles
* context switches
* syscall count

---

## Experiment 4 — kernel vs user CPU

Use flamegraphs:

```
perf record
perf script
```

Observe:

```
tcp_sendmsg
tcp_recvmsg
protobuf parsing
JSON parsing
QUIC encryption
```

---

## Experiment 5 — packet loss test

Add artificial loss:

```
tc qdisc add dev lo root netem loss 1%
```

Test:

* TCP stack
* QUIC stack

Observe tail latency.

---

# 6. Data you should collect

Create tables like:

| Stack | p50 | p99 | CPU cycles | syscalls |
| ----- | --- | --- | ---------- | -------- |

Also measure:

| Metric           |
| ---------------- |
| latency          |
| throughput       |
| CPU              |
| context switches |
| syscall count    |

---

# 7. Data visualization

Use Python:

```
matplotlib
seaborn
```

Graphs to include:

1️⃣ latency CDF
2️⃣ throughput bar chart
3️⃣ CPU usage comparison
4️⃣ syscall count

---

# 8. Research paper structure

Use **standard systems paper format**.

---

# Abstract (150–200 words)

Include:

* problem
* approach
* key findings

Example structure:

```
Modern distributed systems rely on layered network protocols...
We present a measurement-based study...
Our results show...
```

---

# 1 Introduction

Explain:

* microservices growth
* protocol stack complexity
* why overhead matters

Then list **contributions**:

Example:

```
• Empirical comparison of TCP, REST, RPC, and QUIC
• Breakdown of kernel vs user-space overhead
• Controlled microbenchmark framework
```

---

# 2 Background

Explain briefly:

* TCP/IP stack
* HTTP/1.1
* HTTP/2
* QUIC

Keep it short.

---

# 3 Methodology

Very important.

Include:

### Hardware

CPU
RAM
OS version

### Software

Libraries
Versions

### Benchmark design

* payload
* iterations
* concurrency

---

# 4 Experimental Results

Sections:

### Latency

### Throughput

### CPU overhead

### Packet loss performance

Each graph should be explained.

---

# 5 Analysis

Explain **why results look like they do**.

Examples:

* REST slower due to JSON parsing
* gRPC faster due to binary serialization
* QUIC improves tail latency

---

# 6 Related Work

You can search these papers.

Search on **Google Scholar**.

### Good starting papers

**1**
"On the Performance of Remote Procedure Call"

**2**
"The Cost of TCP/IP"

**3**
"QUIC: A UDP-Based Secure and Reliable Transport"

**4**
"A Performance Evaluation of QUIC"

**5**
"Kafka: A Distributed Messaging System for Log Processing"

Even if Kafka is not used, it is related to messaging overhead.

---

# 7 Threats to Validity

Mention limitations:

* single machine
* loopback network
* specific implementations

---

# 8 Conclusion

Summarize findings.

Example:

```
This study shows how protocol stack design influences performance overhead...
```

---

# 9 Reproducibility

Include:

* GitHub repo
* scripts
* configs

---

# 10 Suggested GitHub repo structure

```
network-stack-bench
│
├── tcp
├── rest
├── grpc
├── quic
├── scripts
├── plots
└── paper
```

---

# 11 Timeline recommendation

Week 1
Implement protocols

Week 2
Run experiments

Week 3
Analyze results

Week 4
Write paper

---

# Final advice

Your success depends on **three things**:

1️⃣ identical test conditions
2️⃣ explaining results clearly
3️⃣ good graphs

Coding is the **easy part**.

---

If you want, I can also show you the **exact minimal code architecture** (so all four stacks share the same benchmarking framework). That will make your experiments **much cleaner and easier to analyze.**
 ^M9hfm5dN

Lecture 2 ^7zghuciT

Lecture 3 ^A728Atei

Lecture 4 ^9DFfWfkv

Lecture 5 ^RsAnsv1a

https://www.youtube.com/watch?v=PiEq1CoP0ds ^lRkfdJqG

## Embedded Files
c65ca810f19f3fa8b38b99d4fcf05006dc92ced5: [[9f302bd091c90544027bd68c5dadd4aaa7f314246f6f595b032fccca09fa99fa.png]]

5c06dff8c63969a86e1b50e7a951b41551d88922: [[a477063ecc56aa3084568f1139d8862d6fe82089df618f58e2e06af45aa6f37b.png]]

8c429e0283990b16cb1b7c1f173df2387c07eefc: [[bf3ce4973d30f061c9f10c855b87bae8c4fbc0e1c4700436f2fada47dc5089f7.png]]

60650af8f20386a5c7926598521206d26c203645: [[e21c9ff3b316f38173f42b13c23e64d81bddf6306833ebc5e21002466269f5cb.png]]

9210bd4850a6cfb2cb8c38f6bfa7f2668fe892cb: [[8fc26ccb2d4e6160d43ce902f303eda26ca09de407ab8f5150b4042b215dbbce.png]]

89ab49fe517f3e510654c6187e75da17d9da6261: [[caf08a8862ebde94736795d3deee826753c78529d09235b8fb99ce9aef0cb9d7.png]]

cd1b255e87db62c45aea36ea89a4b429a101f06e: [[9c2150512326a935315b8a2b7a7944c13aba35e84501435631be589b790c27cc.png]]

81e1dabb005987aa83b9b002fde0feb7c11ebed7: [[4542081335bb151c6047bbfc23cb2b26975bb95c766214535a671aa68b4b2431.png]]

80cd4ae398ae6c57915e569b80988af328a90672: [[5fad2e8ddc174e748091f574d4940cdcc675c0c831ae62045b245ff6c4641622.png]]

de8f49ce6389c784c4d54fd4bb7232ea2ea6e311: [[Pasted Image 20260425083952_935.png]]

bb9cdced2d6403d546e4448340acdb7f6dab2267: [[Pasted Image 20260425084019_720.png]]

c47d51b2d33511d894f4c5ceef7d3a3e5c22dbb5: [[Pasted Image 20260425084109_277.png]]

5211b543e8a79861d88d801e13cb3ecbfb3888af: [[Pasted Image 20260425084214_007.png]]

49c284463c67956eaae4a898cbdfa5fa2d26dd3f: [[Pasted Image 20260425084338_370.png]]

2da79aa78b10c35c19d8a0e1142202388a30b2b0: [[Pasted Image 20260425084359_237.png]]

9351f9e276400b7196686014d8b202280772a54e: [[Pasted Image 20260425084432_185.png]]

a375cd2cdeb5fd7dd30864f2f0b19b4f855d8f37: [[Pasted Image 20260425084453_363.png]]

6179fff32ef5913c0475bd6dc527ebbe0722b7be: [[Pasted Image 20260425084713_541.png]]

d271df8b6dfc36737fd37d74602c75fc62db28f8: [[Pasted Image 20260425085529_291.png]]

2ebcf6e18dfd8dc5e11eb5451376b8438d8086fd: [[Pasted Image 20260425085557_288.png]]

12c9b8b6d6be7f1ca2f58a0085bbc8c6c81fef82: [[Pasted Image 20260425085612_653.png]]

c7090417c40efc9cdeb86f3ddf0b9e8ad0f45c94: [[Pasted Image 20260425085649_579.png]]

1028da773db2bf3878f38c76229b6cb79cd6ca0e: [[Pasted Image 20260425090244_990.png]]

50fcad736d0f74735d846006aa4a819244f3fc47: [[Pasted Image 20260425090308_101.png]]

4c5edaf8b80d51f642447393733f81f4dbdf99fe: [[Pasted Image 20260425090332_018.png]]

0b8157b74207d049805c3a711b0a73c0ebdd66b5: [[Pasted Image 20260425090417_982.png]]

da5f1f3a855aea12e8068eb0af51ee1a01f2e13f: [[Pasted Image 20260425090955_935.png]]

4f72425c25409ace2e5bad8847ef81a2bdf67c9d: [[Pasted Image 20260425091103_710.png]]

6df258c9036f8d57f4295fdfa68c55fc824c3098: [[Pasted Image 20260425092012_347.png]]

b6c9907ff75b7fcfd88b5b2b8fc8dc131a8a5a58: [[Pasted Image 20260425092052_559.png]]

1173a44f30d295fbfa8d6f3d20ac97bbf43fc80f: [[Pasted Image 20260425093239_759.png]]

027dd8c2e11e5cc362a0eab70010c3aaa7c56bd5: [[Pasted Image 20260425093805_310.png]]

d2220744e43af1ed19e2f5726c8d69b03daa56f7: [[Pasted Image 20260425093912_991.png]]

19faac5078d9562e78be8fa3b8abfc1f048c3a3d: [[Pasted Image 20260425093913_009.png]]

3b517d7fdd5050f2b2252f1c7d178e57794bd889: [[45c34207d9aa07780a6bbb135652c1468fcedc8d5c7d6ac62e755b46a5df3214.png]]

cb52d0651e6cf902b299910be215963a5d6535a5: [[3e7234a66a37b47c233920459e8e30c3244e8e6dd6d38c0d0179ae1c9dbeb761.png]]

11cc9b653ca4681be5bd60114eb3b8f454e0e157: [[Pasted Image 20260425094740_548.png]]

63d9d5072167997a399e43db651e55d7b2cb64a7: [[Pasted Image 20260425094842_376.png]]

cb3676085eb1d3fbcee88445b43451498eeec75a: [[Pasted Image 20260425095139_108.png]]

e591b6b0e9c5e6358928fd0b9bbf6773602a6952: [[Pasted Image 20260425095304_662.png]]

ea936d238b95f2af17a40388cc118dd5087429ba: [[a82e37630337c81ef5a9036555129efa0badcfd43b45ffff5fe7fc9e3c2b6b25.png]]

a2b4cf76d6e5b2726994a0ab58ee006b33deb426: [[dacb332c77d253df7d9b8b05b6e16127cf2cc75d1a29e5392fbb48a25836e5f1.png]]

8d0ac6e5f2c7fda8aff9c1490ffd133b0c9ed510: [[Pasted Image 20260425095421_524.png]]

92f13f242600612b7ca816811fad7c6b4da3ce40: [[Pasted Image 20260425095508_336.png]]

2111d954c4e0d7b3bdb6e0a9e0e70fc89fcdfa60: [[Pasted Image 20260425095656_589.png]]

5ddf43c7891b940fa8d6b7540dee0eed56c7202f: [[Pasted Image 20260425095723_128.png]]

9bbe6294901faa0fd4fcfa18b5e2eadbd0f3cc7d: [[Pasted Image 20260425095818_688.png]]

42b530894a62009f1e14b3a2beb1ca1d6d280cee: [[08c9d98d98f3bd7de619ada66bd2f77f5cb1c3158a985f4c1a6c0bc5d443f3c1.png]]

fc8b00ffe5f1a474443bb54aa8120351c0a4b6a1: [[22f2bf5a2430bb18c3349536e0d64d3fc58dfbfb5c85187fcea0bc2bff8a7dcf.png]]

6811c88f39b906bfffde8b457af0f8712c40a9f7: [[ec867897086570c048a7fac11646f146b7572b56b11b75bede2c5de413697730.png]]

8d354380c37709ea7584a0e3740c5e8367c2558c: [[1e657c60ace92e8e8eb75e093b5facf46c109c13d347c99517f0e4ba0e35c257.png]]

a69b3edb6c053a59307a2aaad11099d0770c2a64: [[7930610c2cf6c317a74f90874322acd147a59409dc40b2436d09900c47615bbb.png]]

fbd3620c474ce243e33f44ed8e5e147e87c7275f: [[d0d3c65daee5775195e09fdd24a594323307cc82eb855fac5440ae29cde7784c.png]]

c1075b727008a8fe5040418e744bce06554af94d: [[0f4169b081e11406c238dd30896f17ca570721d230ac35bbda1f994c9be186c4.png]]

680736188c51f7ead5c3793fa4fc0f547d966a38: [[5e5b5741a4df80b498493b08d0c0a69d70cfe11d906f340e619fdc66043cafa3.png]]

08e35d4b6d071f33d6b7b73e49e719bd2f95a952: [[b1bc21ab125ed4f31273d15214172928857c76f7b3fbbfc223281b24feb0aed2.png]]

1a881bfe004b2642d587d8b38df7dd773a5b53ac: [[620e9b393f37482ef7ab5be49969073e9906267b8cf794059b119b6f276f6ef7.png]]

0364ceec4795841b32d96180069489ceac937b76: [[6b4d362d988e5ee0a9ea3713850c9b1c55451070d2ca1daf4db095c8f99d80ac.png]]

6b5a305e7a3375b26bf70ded72f77c6eb43af465: [[Pasted Image 20260425102700_096.png]]

7ca1567afa0d4f2ad0995f9e7311122b381c56f5: [[Pasted Image 20260425102752_020.png]]

d84eef6b2ecf51882f369e881b75e82f3d303953: [[029a28d993aca3d9363132723f1714f75440cda8584a76c3e43cfac56df2c8f8.png]]

1b5377b64569ab76731343c9f3dced9aa7ac2e00: [[219eed61956b9bb7b9d723cc324b7e6d41c07fb0b91817cd2b3fd4a1b76ef788.png]]

d087bd5f973539f35a4a73addc29477a9051e260: [[25bf2a3e259b3eeb640edc8dd0c2f9027448cd03fefb82ba05c1f84d3b0b1538.png]]

ba3d57dd919fc1c3176317882a3e4de7beb51b6e: [[Pasted Image 20260425103952_115.png]]

04e3103dc9cf75b9716a47d17206d8e7487e8f7b: [[Pasted Image 20260425104016_288.png]]

e6dfe213153ffdacd06be7bb8ac00b365bc08043: [[Pasted Image 20260425104054_856.png]]

5e78e23eda552131025a91fdf06449457310f5fc: [[Pasted Image 20260425104206_664.png]]

98c7ea4365cd1a2f8a0f5d980c7f2ace339aac6e: [[Pasted Image 20260425104254_662.png]]

09f7636a37adc4f42d5e7fe4a3d03bc0299e06c3: [[Pasted Image 20260425104447_376.png]]

02fcac60a7a2a3cc583a7efd6a16e58cc5f559e1: [[Pasted Image 20260425104509_198.png]]

2e9e46ab8dea3472dcd70ecc5f26b14623f215d4: [[Pasted Image 20260425104822_464.png]]

fe792b925d6014fbdbb1160dbe6b346bc6f11ee3: [[Pasted Image 20260425113735_300.png]]

37d5e1cc171e0aadffb9a638e1c10591ab43638f: [[Pasted Image 20260425115004_765.png]]

2d90147372d97444fe16fcf063a582889dcfb155: [[034451e06f3a69018a50b847f3eec4d504371ade5e856d066c7cef0d8c642bb5.png]]

afa3f7cce998fb3eff3dfc2fb415c8dbf88edfb7: [[Pasted Image 20260425115036_476.png]]

83c1f50463d91cb8ace506b8e150049c01b4e793: [[eeba304739fe3ec58efbcd112274f724bdf09a28d3629d2bcd2ae72097cff31c.png]]

07c613ef7528b76c427f12be8a846a6f3df23c4a: [[Pasted Image 20260425115227_812.png]]

62b0430bd21f3cc72f7a41cc74e04461297b0e23: [[Pasted Image 20260425120034_294.png]]

e12db8882db29767a6546572538c43ef51eb9327: [[Pasted Image 20260425120100_296.png]]

af3af815b3ce0d0b148ef806df174b69bea972c1: [[Pasted Image 20260425120125_699.png]]

cd675d93500e511dd747c79360b9dc0cf5685525: [[Pasted Image 20260425120306_674.png]]

1b408cdad29032f3a8269eb958d3bb580fcdcbdc: [[Pasted Image 20260425120838_695.png]]

9077574913d227bb0eb62e6b5dd344ef23b383c6: [[02e4fef1558d8c44d3b259213a68cc07377b23b3f35669fc9c18e99abe456d42.png]]

524117cb189b16fca758496c1249f96fca78167d: [[cfae4014495a7080abd974f7adacb95a6aee748b772b0e71882d34c624c5aec6.png]]

0fe29480e35001e610a14c0bbe14ab0a4c324cf1: [[76c2af1e198211461eb21373272e0cae28c60a9a3dfc5fb37c55ed1e42d35f15.png]]

73753c2a4871a0351213c8ca85e911bc5ec29dd2: [[Pasted Image 20260425124158_153.png]]

833d2caba248007abbb93fde68c7e0b90a2fa93d: [[Pasted Image 20260425124531_785.png]]

a3ac5a8ff36abb2a82a29df618f03fe655356f28: [[Pasted Image 20260425124603_851.png]]

d70bf216aad70d74fbca74d1cab0dcfa2bab7c60: [[Pasted Image 20260425124712_235.png]]

f23b3c93a52f77a1ee48e81df64b522cce970a81: [[Pasted Image 20260425124843_114.png]]

580afb0428347a02217e9d90bd3fe16d6ce77691: [[Pasted Image 20260425124910_965.png]]

8d680a20dfcf0613e817c9a0bea1ae8e72fa1ce6: [[Pasted Image 20260425124941_517.png]]

71a97ad6affa9a2fd7a7bab12627836abb58d47f: [[Pasted Image 20260425125022_478.png]]

9ea6a47f3f5f92b57a0e28c39940b372f7442bb2: [[7002a94edcc8412a0a3af5ed2484aa271e60f9167072365cd39982c50120b83f.png]]

27fa113b98c520d648fce96853ee199a97a4a1a7: [[0bc6008a5e84d0074b81e47fc9e5788974ea12e7c137344dec135e04cc24be70.png]]

adcf5afba325171af08d648cc104961e4fe6420c: [[456adda8892c29da242aefbe0cbe09a1d39f507c492898bd8da6ba6ade0534f9.png]]

dafa51919de993fba55a946ac597bf8d0dd5f4c5: [[5f69139ede7c73a7ad320d0a92e88cb3cc7d081cd882c63c41f434b5cc1bc433.png]]

aa78dbd92b1c7b2a8f4c82a041a7ca20ef8f4208: [[5bcbedd7ca788a138aada1cd61f45e3d121f8bf594319af67b28f410167e958d.png]]

ab37a66c0105680ef29e3c872379262a8d87c0b8: [[ee97f4ac8ad0accc09f69b017e682da2948eed6bdccf1af683911fbc1ee5ee0b.png]]

07b625eea5d559290e7dd718a556a4340848ea3d: [[a188ac5e212f1d47d14b8f5ab0519b1be6a191e932bc958c6d507c957d566c59.png]]

3abff4b18b5b5e549661068b9198997caf844453: [[f4fadfab292994da12b5a83cbb5fd9998a790abff809da53821add164d6cfa57.png]]

e69638c0b2fd74d90bb89113120133553e8b06f1: [[ddc82f84ab02a0a56f9932a118e754b6bc793f0c68834e23dd053b18aaf2a4dc.png]]

184e59f10074f1ad6751f2aa8b417d43eba51b06: [[Pasted Image 20260425125933_061.png]]

f4b61023efb0121d0af3c74daf2ba4c39b1cb37e: [[Pasted Image 20260425130014_517.png]]

800729d3ce97e087c521aa9f421f5ceadb37c487: [[Pasted Image 20260425130051_192.png]]

8fe61c756323c0d085f7f9c6a253e174bedb4a26: [[Pasted Image 20260425184750_104.png]]

149fe0a9727ae0e5a0bc748ed5d7c713b2c19edb: [[Pasted Image 20260425184907_988.png]]

52d2a4ac8162014123abf44995ae69c641f04a9d: [[Pasted Image 20260425184947_020.png]]

6d5f9e8d6d2a44a9996e539d0432e1af9045e00f: [[Pasted Image 20260425185139_573.png]]

3cecaac90171e7cbe96d1f5e435516abe8228393: [[c6dafb9405290d1f23246178e3e19ca8bce45cbb17b2f25506964f45957b7075.png]]

926434f2af072d37e4cc244a4bfadd01e3bab3a5: [[172a0d1945defcc7d0059673590c563acab3617bae102bd196dd9ae3e4a15574.png]]

9fe1ee64c263c0e75c5c9e26420c5af626b968e1: [[af1e1f2f7d7a9606898dccb4b574d8c23db59c5dd5aaaa1ef2bfd77729491a3b.png]]

c273c4f9bcc560aecad0295dc34c46a1a3957084: [[Pasted Image 20260425185448_106.png]]

40e8968b26e8912a3adc56283bb5734ee0c57d0b: [[Pasted Image 20260425185540_806.png]]

de186026e7c3e431a6028364e5e58713d510123e: [[Pasted Image 20260425185834_782.png]]

5fbccbe592728d48588849a9aea6e4d208eae514: [[Pasted Image 20260425185858_401.png]]

6168483443ec15f7285ff217c02a32d8b3f04393: [[Pasted Image 20260425185935_765.png]]

63994b76269b440d75906ba16183f4d505f8a80f: [[Pasted Image 20260425190024_870.png]]

d7bbb536f8124c133c258fc92e543be4bbad9827: [[Pasted Image 20260425190051_330.png]]

03ea692a5040f62a705c54c1feeb6230217e5576: [[Pasted Image 20260425190136_596.png]]

72a1f1613580b230eba6cb3b86e2ad56db6901b8: [[Pasted Image 20260425190152_133.png]]

04024acfc7c90f7b5675aca2e197aef39baf0a35: [[Pasted Image 20260425190216_202.png]]

7d75227bf806cd31c4cc6ec9661627a0aff24c11: [[Pasted Image 20260425190247_851.png]]

7da6f49a397a79cad5a2691fb90f7ad2f72376e2: [[16f745215bf12d58c8dcfe62c9a8c0af85a455a57299a241553b5d60f85abb27.png]]

661765649ea7e585aeaae2b94b90c71b370bd689: [[2ad26e16bc6a9e3be4a53b81e01a860a956d29ec8515a3e7248c38c176381bc9.png]]

bd2e30a8363e7a0ebc5dac744f8604d49a94c4e4: [[28a30212af3079d5bcb2c6b9185c02ff4924bf687e90335eb140ed4be128a1a8.png]]

77bac8677b2b38afdaf28e26383fac673d4c7080: [[Pasted Image 20260425190744_245.png]]

960640322a8b3653e7219f3b79f1f6559c1f017f: [[Pasted Image 20260425202106_388.png]]

2167130a82a80ed1e8e1b4cc6f0752b379b828fd: [[Pasted Image 20260426080205_761.png]]

15bdffd25f362445ccdc3393abd7918adecf4c56: [[d9b820d722fab4e2e2d6a467b326650d2783a64ae48f451103bb8625addfe935.png]]

781a86f047754dd2180d39683437c4f048947cd8: [[a963e0c11f36d53e2906de1df315987f0a2e4b24df9850f40802bf06fc35f2c2.png]]

08e53f4d3785f6c84c411c2fd866d2401914fcdd: [[8e45dfc7150597ade4807291217092a62a5cc87bb7756d659b52c9e5ce4ef894.png]]

9eebbe21b8744e8e4fb54b3f08c5bb9c00a0fe70: [[Pasted Image 20260426080859_907.png]]

8bf218f39c67bbfe64e168884aed879c6156c4b6: [[Pasted Image 20260426080934_277.png]]

d69b2ef184d310718d4644d21d76555db1b34022: [[Pasted Image 20260426081109_114.png]]

7871767aea4bd36c4f461b0ba24bfc1638870f6e: [[Pasted Image 20260426081211_692.png]]

1d0a40d18458ade23a6dbf54a847c6e560bfb4ff: [[Pasted Image 20260426081238_853.png]]

f239efcf1483969f9cd886b2bc1ee8a3726099e9: [[Pasted Image 20260426081326_087.png]]

1de1f49b41b02d80585c32149096c6f5a8ebeca4: [[Pasted Image 20260426081452_507.png]]

a64860b8e728fd0d3fa1bc513233b592670486b9: [[a0f6eb04f938b3bcfc0109a4b0814fbf3e5edc6ed1d55ec1ec8464eec8680e7b.png]]

0bc85f8fa9eb8e2cd6cdd2248422893135130792: [[55b410d0001bf4689c1d7c5a8684428ae6ebc4e579f928a7f3517190ee21db22.png]]

30c0562f77f97125eb1825bdfc5345d3b182e956: [[Pasted Image 20260426081958_658.png]]

efcf6ed9e50d6b6d2f98777a250b3940f25761c9: [[f891a93e3af0a1e7034fb0a674699dd649857e6a8cfa90d56d644312ea15a775.png]]

5b682669d4335393cb5262173c0ebe4edfb65a7c: [[00d490e950bc84d712ac3281d5918f4393672486135d0b856edf5cedbd32b133.png]]

5bc2c975f5aa7f0595fef76320b602a3eebf974c: [[Pasted Image 20260426082447_698.png]]

d1cc9720baf12b141c6213432b46c64f49269b7c: [[7118c6208ae5010c1317b9bf5c7aa14f1b0cbdb25c073075763c77fe51d3a137.png]]

d442c0c40c4cb5c0b28ed1426eca8d68bd8fc33e: [[55570dbfe4b73e09bb30ede582a83b838bfe975f179c64123709927176976cdb.png]]

8535e27b115b307463acc6650925514d101f6f5c: [[Pasted Image 20260426085653_093.png]]

dcfc752b4097e3cf76b21cd4dec3fbb222020a78: [[Pasted Image 20260426085724_193.png]]

acdd129ecb6408a00dcfc779627932b11029e172: [[Pasted Image 20260426085759_010.png]]

bf7cf5e99728e504b994064a2141209fc548aecd: [[Pasted Image 20260426094937_437.png]]

3935b0cd79b5b9cb69621090208b1c095942b9fc: [[590bf31965fde0f066d5053d20dbbef459dc1693d350035ebd7d00083ca8853c.png]]

29f7cdc11142e5e33540390fcb56aa8713f92580: [[dedd228e1aaf53775d964f88f2822b8cf30ab1d05a06811f41114334cb982560.png]]

312a526c45b06e9c72eaf2fefa5236d7cfa19c9f: [[3411677b6ec3d23dae55839dca3712643e80790d6ae6c7451af83584e2397dfe.png]]

5c184d84889618da3a7c86723223bfed463c171b: [[00542c1fde6e66ecd80c5c15f1fc367ca8039005c93bc8873556c5d457316837.png]]

f9ad1d2cf81c0a65ad8aa39bca54caa73a2a8e6c: [[80ac0315d7e74fbf766ec7b3e54777023c59a6de4ac5f5fe643621a7fc0739b6.png]]

8dac3d77db2b5bb1647fb5257ccf2083d727487b: [[d620f55becd19a08beb4e196447a36c46a09dc56c16527fe285d2e5bf3bfe848.png]]

765d5645f7a71db60f0ef05a6001893d8b863d3c: [[Pasted Image 20260426095605_852.png]]

891a6bb62eb47af3c3ab2fdac6d7708241795667: [[Pasted Image 20260426095635_312.png]]

af938ae44b32579661764a40ddf523c503d0a7d8: [[580ae7a4b2ee6b8c5aa17a1818258567c9a0861f2bdcd5de3c1ac6d1eadbef09.png]]

d8aa1696e8b8dcca83414158c358deed48825fd0: [[92b51bb51cad663e556757d5a4b640655b1de9229298ba1032d3304498b4b40b.png]]

03dbe2b627fafb01502c05360fd2db8f2d6fca66: [[Pasted Image 20260507192435_666.png]]

cc9f453ead08b641fd36b3e011f9d83a28700686: [[Pasted Image 20260507192508_590.png]]

cafa0fcbf75d6b1505371414c494fb74043f8436: [[Pasted Image 20260507192606_650.png]]

3e4c5613d09375f748080d4892a34af996ec9db3: [[Pasted Image 20260507192730_361.png]]

94434d02ca0f93a1a2caf23bd93d718c1c320b5a: [[Pasted Image 20260507192949_976.png]]

fca013d3c351699f2c50ca52a43a9dec9aaa028c: [[Pasted Image 20260507193022_508.png]]

0015abcbc8135182027e1b9dea5f730da6631d93: [[Pasted Image 20260507193049_833.png]]

125730cb1ea57a3101a1c38c7ea6ced1c3c1750e: [[Pasted Image 20260507193244_874.png]]

1d48008927febe3a7b6d5341a6582e66ac070637: [[Pasted Image 20260507193302_284.png]]

cc3707f3df550cde1f95e0bb5eddf14d8cf57ef7: [[Pasted Image 20260507193424_225.png]]

118241c6a357f4dd4024faa399c19c93adb7200d: [[Pasted Image 20260507193543_676.png]]

d8cfc8d6d5d135d77f343265289bdaa01e560285: [[Pasted Image 20260507195258_776.png]]

9a9cea446da1e189910f44476898fa8540ba455f: [[Pasted Image 20260507195324_012.png]]

%%
## Drawing
```compressed-json
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
```
%%