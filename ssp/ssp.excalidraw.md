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
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=
```
%%