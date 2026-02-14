---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Flat profile:

Each sample counts as 0.01 seconds.
  %   cumulative   self              self     total           
 time   seconds   seconds    calls   s/call   s/call  name    
100.00     37.12    37.12        1    37.12    37.12  bubble_sort
  0.00     37.12     0.00        1     0.00     0.00  generate

 %         the percentage of the total running time of the
time       program used by this function.

cumulative a running sum of the number of seconds accounted
 seconds   for by this function and those listed above it.

 self      the number of seconds accounted for by this
seconds    function alone.  This is the major sort for this
           listing.

calls      the number of times this function was invoked, if
           this function is profiled, else blank.

 self      the average number of milliseconds spent in this
ms/call    function per call, if this function is profiled,
           else blank.

 total     the average number of milliseconds spent in this
ms/call    function and its descendents per call, if this
           function is profiled, else blank.

name       the name of the function.  This is the minor sort
           for this listing. The index shows the location of
           the function in the gprof listing. If the index is
           in parenthesis it shows where it would appear in
           the gprof listing if it were to be printed.


Copyright (C) 2012-2024 Free Software Foundation, Inc.

Copying and distribution of this file, with or without modification,
are permitted in any medium without royalty provided the copyright
notice and this notice are preserved.


                     Call graph (explanation follows)


granularity: each sample hit covers 4 byte(s) for 0.03% of 37.12 seconds

index % time    self  children    called     name
               37.12    0.00       1/1           main [2]
[1]    100.0   37.12    0.00       1         bubble_sort [1]
-----------------------------------------------
                                                 <spontaneous>
[2]    100.0    0.00   37.12                 main [2]
               37.12    0.00       1/1           bubble_sort [1]
                0.00    0.00       1/1           generate [3]
-----------------------------------------------
                0.00    0.00       1/1           main [2]
[3]      0.0    0.00    0.00       1         generate [3]
-----------------------------------------------

 This table describes the call tree of the program, and was sorted by
 the total amount of time spent in each function and its children.

 Each entry in this table consists of several lines.  The line with the
 index number at the left hand margin lists the current function.
 The lines above it list the functions that called this function,
 and the lines below it list the functions this one called.
 This line lists:
     index      A unique number given to each element of the table.
                Index numbers are sorted numerically.
                The index number is printed next to every function name so
                it is easier to look up where the function is in the table.

     % time     This is the percentage of the `total' time that was spent
                in this function and its children.  Note that due to
                different viewpoints, functions excluded by options, etc,
                these numbers will NOT add up to 100%.

     self       This is the total amount of time spent in this function.

     children   This is the total amount of time propagated into this
                function by its children.

     called     This is the number of times the function was called.
                If the function called itself recursively, the number
                only includes non-recursive calls, and is followed by
                a `+' and the number of recursive calls.

     name       The name of the current function.  The index number is
                printed after it.  If the function is a member of a
                cycle, the cycle number is printed between the
                function's name and the index number.


 For the function's parents, the fields have the following meanings:

     self       This is the amount of time that was propagated directly
                from the function into this parent.

     children   This is the amount of time that was propagated from
                the function's children into this parent.

     called     This is the number of times this parent called the
                function `/' the total number of times the function
                was called.  Recursive calls to the function are not
                included in the number after the `/'.

     name       This is the name of the parent.  The parent's index
                number is printed after it.  If the parent is a
                member of a cycle, the cycle number is printed between
                the name and the index number.

 If the parents of the function cannot be determined, the word
 `<spontaneous>' is printed in the `name' field, and all the other
 fields are blank.

 For the function's children, the fields have the following meanings:

     self       This is the amount of time that was propagated directly
                from the child into the function.

     children   This is the amount of time that was propagated from the
                child's children to the function.

     called     This is the number of times the function called
                this child `/' the total number of times the child
                was called.  Recursive calls by the child are not
                listed in the number after the `/'.

     name       This is the name of the child.  The child's index
                number is printed after it.  If the child is a
                member of a cycle, the cycle number is printed
                between the name and the index number.

 If there are any cycles (circles) in the call graph, there is an
 entry for the cycle-as-a-whole.  This entry shows who called the
 cycle (as parents) and the members of the cycle (as children.)
 The `+' recursive calls entry shows the number of function calls that
 were internal to the cycle, and the calls entry for each member shows,
 for that member, how many times it was called from other members of
 the cycle.


Copyright (C) 2012-2024 Free Software Foundation, Inc.

Copying and distribution of this file, with or without modification,
are permitted in any medium without royalty provided the copyright
notice and this notice are preserved.


Index by function name

   [1] bubble_sort             [3] generate ^UEkmsjCt

Samples: 267K of event 'task-clock:ppp', Event count (approx.): 66973750000
  Children      Self  Command   Shared Object            Symbol
+   17.85%     0.00%  cc1       [unknown]                [.] 0000000000000000                                                          
+   15.58%     0.00%  cc1       [unknown]                [.] 0x0000000900000000                                                          
+   15.38%     0.00%  cc1       [unknown]                [k] 0x00007b616fa03b20                                                          
+    9.24%     0.00%  cc1       [unknown]                [.] 0xffffffff9c400bc7                                                          
+    9.24%     0.00%  cc1       [unknown]                [.] 0xffffffff9c2493d3                                                          
+    7.42%     0.00%  cc1       [unknown]                [.] 0xffffffff9b0d6e19                                                          
+    7.00%     0.00%  cc1       [unknown]                [.] 0xffffffff9b42e74a                                                          
+    6.64%     0.00%  cc1       [unknown]                [k] 0x000000001d53d070                                                
+    6.64%     0.00%  cc1       [unknown]                [.] 0x0000005b00000155                                                 
+    6.63%     0.00%  cc1       [unknown]                [.] 0x00007b616f081f18                                                   
+    6.58%     0.00%  cc1       [unknown]                [.] 0xffffffff9b42e404                                                           ^KTujU8hp

iiitb@iiitb:~/ssp/exe3$ ./pi 2000000000
Thread 9: partial=-3.955287508593021
Thread 1: partial=-5.226964253479011
Thread 0: partial=7.922334582711562
Thread 2: partial=4.668256291328401
Thread 4: partial=4.269473313815297
Thread 6: partial=4.096835477228384
Thread 8: partial=3.993819704988813
Thread 5: partial=-4.169957435081242
Thread 3: partial=-4.416979758717295
Thread 7: partial=-4.039937761111522

TOTAL TERMS: 2000000000
pi_est (MUTEX) = 3.141592653090365
pi_accum       = 0.785398163272591 (before *4)
elapsed        = 11.472 sec

Expected pi ~ 3.141592653589793 ^umDpb4ZI

iiitb@iiitb:~/ssp/exe3$ perf stat ./pi 2000000000
Thread 8: partial=3.993819704988813
Thread 4: partial=4.269473313815297
Thread 5: partial=-4.169957435081242
Thread 3: partial=-4.416979758717295
Thread 2: partial=4.668256291328401
Thread 1: partial=-5.226964253479011
Thread 0: partial=7.922334582711562
Thread 9: partial=-3.955287508593021
Thread 6: partial=4.096835477228384
Thread 7: partial=-4.039937761111522

TOTAL TERMS: 2000000000
pi_est (MUTEX) = 3.141592653090365
pi_accum       = 0.785398163272591 (before *4)
elapsed        = 11.602 sec

Expected pi ~ 3.141592653589793

 Performance counter stats for './pi 2000000000':

         22,920.28 msec task-clock                       #    1.975 CPUs utilized             
            11,964      context-switches                 #  521.983 /sec                      
                21      cpu-migrations                   #    0.916 /sec                      
                84      page-faults                      #    3.665 /sec                      
   <not supported>      cycles                                                                
                 0      stalled-cycles-frontend                                               
                 0      stalled-cycles-backend                                                
   <not supported>      instructions                                                          
   <not supported>      branches                                                              
   <not supported>      branch-misses                                                         

      11.606649522 seconds time elapsed

      22.886246000 seconds user
       0.029919000 seconds sys ^tXqWVNLA

 ~/Downloads/term 2/subs/ssp/exe3/ ./pi_1 50000000000
Thread 2: partial=0.000000000033333
Thread 5: partial=0.000000000006667
Thread 6: partial=0.000000000004762
Thread 3: partial=0.000000000016667
Thread 4: partial=0.000000000010000
Thread 9: partial=0.000000000002222
Thread 7: partial=0.000000000003571
Thread 1: partial=0.000000000100000
Thread 8: partial=0.000000000002778
Thread 0: partial=3.141592653388201

TOTAL TERMS: 50000000000
pi_est (MUTEX) = 3.141592653568201
pi_accum       = 0.785398163392050 (before *4)
elapsed        = 8.230 sec

Expected pi ~ 3.141592653589793 ^MTsghjvv

 ~/Downloads/term 2/subs/ssp/exe3/ ./pi 50000000000
Thread 8: partial=4.637594869622835
Thread 9: partial=-4.599062673130708
Thread 6: partial=4.740610642053787
Thread 2: partial=5.312031456537959
Thread 5: partial=-4.813732600002757
Thread 1: partial=-5.870739418784577
Thread 7: partial=-4.683712925840922
Thread 3: partial=-5.060754923830659
Thread 0: partial=8.566109748100578
Thread 4: partial=4.913248478832482

TOTAL TERMS: 50000000000
pi_est (MUTEX) = 3.141592653558017
pi_accum       = 0.785398163389504 (before *4)
elapsed        = 8.407 sec

Expected pi ~ 3.141592653589793 ^YFnNJkU8

 ~/Downloads/term 2/subs/ssp/exe3/ ./pi_1 50000000000
Thread 9: partial=0.000000000002222
Thread 3: partial=0.000000000016667
Thread 8: partial=0.000000000002778
Thread 4: partial=0.000000000010000
Thread 0: partial=3.141592653388201
Thread 5: partial=0.000000000006667
Thread 7: partial=0.000000000003571
Thread 2: partial=0.000000000033333
Thread 6: partial=0.000000000004762
Thread 1: partial=0.000000000100000

TOTAL TERMS: 50000000000
pi_est (MUTEX) = 3.141592653568201
pi_accum       = 0.785398163392050 (before *4)
elapsed        = 7.735 sec

Expected pi ~ 3.141592653589793 ^UT52koia

## Embedded Files
4e4a5a57fe9eac2e0dbd4ee28488e7659eb1cd6f: [[Pasted Image 20260207104118_584.png]]

d41fc492d748be62bba7243b03dea34b9a88d90e: [[Pasted Image 20260207104236_862.png]]

d964e79ca4dc890a1e46b1ee5f309d48fa99167a: [[Pasted Image 20260213104129_045.png]]

6e095de632b26bd3a1f3691ac0d6025b90ffc72f: [[Pasted Image 20260213105845_549.png]]

%%
## Drawing
```compressed-json
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
```
%%