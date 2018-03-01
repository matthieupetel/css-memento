CSS memento
===========

Introduction
------------

This project is my list of CSS code explanations and reminders.

CSS selectors
---------------

### :nth-child

```
.class:nth-child(2n+1) {}
```

**Useful pseudo selector that targets elements according to a counter.**

Synthax: `:nth-child(An+B)`, where `A` is the step between the occurrences 
of the elements, and `B` is the gap between the starting point of the list (which begin at 0).

**Examples:** 

`:nth-child(3)` selects every matching element in 3rd position of the counter. Represents element 3.

`:nth-child(2n)` or `:nth-child(even)` selects every matching element in 2nd position of the counter repetitively,
starting from the beginning. Represents elements 2, 4, 6, 8, etc.

`:nth-child(2n+1)` or `:nth-child(odd)` selects every matching element in 2nd position of the counter repetitively,
starting from the 1st element. Represents elements 1, 3, 5, 7, etc.

`:nth-child(4n+3)` selects every matching element in 4th position of the counter repetitively,
starting from the 3rd element. Represents elements 3, 7, 11, 15, etc.

`:nth-child(n+5)` selects every matching element from the 5th position of the counter. Represents 
elements 5, 6, 7, 8, 9, 10, etc.

`:nth-child(-n+5)` selects every matching element between the 1st and the 5th position of the counter. Represents 
elements 1, 2, 3, 4, 5.

Remark: in order to select every matching element between the 1st and the 5th position of the counter starting from 
the end, use `:nth-last-child(-n+5)`

**How it works:** 

With the synthax `An+B`, `A` is the step in the loop, and `B` is the index at which 
the loop will begin.  
It is calculated as follows:  
`(Axn)+B`

With the example of `3n+2`:  
(3x0) + 2 = 2  
(3x1) + 2 = 5  
(3x2) + 2 = 7  
(3x3) + 2 = 9  
(3x4) + 2 = 11  
...

With the example of `-n+3`:  
-0 + 3 = 3  
-0 + 3 = 2  
-0 + 3 = 1  
-0 + 3 = 0  
-0 + 3 = 0  
...

To summarize in a table:  

| n         | 2n+1      | 4n+1      | 4n+4      | 4n        | 5n-2      | -n+3      |
|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
| **0**     | 1         | 1         | 4         | -         | a         | a         |
| **1**     | 3         | 5         | 8         | 4         | a         | a         |
| **2**     | 5         | 9         | 12        | 8         | a         | a         |
| **3**     | 7         | 13        | 16        | 12        | a         | a         |
| **4**     | 9         | 17        | 20        | 16        | a         | a         |
| **5**     | 11        | 21        | 24        | 20        | a         | a         |
