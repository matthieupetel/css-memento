CSS memento
===========

Introduction
------------

This project is my list of CSS code explanations and reminders.

CSS selectors
---------------

### :nth-child

```css
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
-(1x0) + 3 = 3  
-(1x1) + 3 = 2  
-(1x2) + 3 = 1  
-(1x3) + 3 = 0  
-(1x4) + 3 = 0  
...

To summarize in a table:  

| n         | 2n+1      | 4n+1      | 4n+4      | 4n        | 5n-2      | -n+3      |
|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
| **0**     | 1         | 1         | 4         | -         | -         | 3         |
| **1**     | 3         | 5         | 8         | 4         | 3         | 2         |
| **2**     | 5         | 9         | 12        | 8         | 8         | 1         |
| **3**     | 7         | 13        | 16        | 12        | 13        | -         |
| **4**     | 9         | 17        | 20        | 16        | 18        | -         |
| **5**     | 11        | 21        | 24        | 20        | 23        | -         |


Flex shorthand property
-----------------------

```css
.flex-item {
    flex: 0 1 auto; /* initial values */
}
```

The `flex` shorthand property applies rules on a flex item to tell how to handle dimensions
to fit inside its flex container.

It can accept up to 3 properties (one min) which stand for respectively `flex-grow`, `flex-shrink` and `flex-basis`.

**With one value:**

Base values are:  
- `flex: auto`: stands for `1 1 auto`, item will grow and shrink if necessary to fit all the space available.
- `flex: initial`: stands for `initial initial initial`, item will not grow but will shrink if necessary not to overflow its
container.
- `flex: none`: stands for `0 0 auto`, item will neither grow nor shrink.

One unitless value: flex-grow
- ex `flex: 2`: sets `flex-grow` to `2`, `flex-shrink` to `1` and `fex-basis` to `0`.

One value with unit: flex-basis  
- ex `flex: 50px`: sets `flex-grow` to `1`, `flex-shrink` to `1` and `flex-basis` to `50px`.

**With two values:** the value with unit is for `flex-basis`
- ex `flex: 2 2`: sets `flex-grow` to `2`, `flex-shrink` to `2` and `fex-basis` to `0`.
- ex `flex: 1 300px`: sets `flex-grow` to `1`, `flex-shrink` to `1` and `fex-basis` to `300px`.

**With three values:**
- ex `flex: 2 2 300px`: sets `flex-grow` to `2`, `flex-shrink` to `2` and `fex-basis` to `300px`.

To summarize in a table :  

| flex:         | grow      | shrink    | basis     |
|---------------|:---------:|:---------:|:---------:|
| **auto**      | 1         | 1         | auto      |
| **initial**   | initial   | initial   | initial   |
| **none**      | 0         | 0         | auto      |
| **2**         | 2         | 1         | 0         |
| **50px**      | 1         | 1         | 50px      |
| **2 2**       | 2         | 2         | 0         |
| **1 300px**   | 1         | 1         | 300px     |
| **2 2 300px** | 2         | 2         | 300px     |
