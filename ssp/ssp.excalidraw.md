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

## Embedded Files
4e4a5a57fe9eac2e0dbd4ee28488e7659eb1cd6f: [[Pasted Image 20260207104118_584.png]]

d41fc492d748be62bba7243b03dea34b9a88d90e: [[Pasted Image 20260207104236_862.png]]

%%
## Drawing
```compressed-json
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
```
%%