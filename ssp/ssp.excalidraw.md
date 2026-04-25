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

%%
## Drawing
```compressed-json
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=
```
%%