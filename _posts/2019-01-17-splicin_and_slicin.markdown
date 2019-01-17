---
layout: post
title:      "Splicin' and Slicin'"
date:       2019-01-17 15:45:51 +0000
permalink:  splicin_and_slicin
---

## Learning Javascripts Array Methods: .slice() and .splice()

Today we'll go after a rudimentary topic in Javascript and see if we can't lay it out very clearly. 

.slice() and .splice() are two array methods in javascript that return pieces of the array. Slice does so non-destructively (ie. leaving the original array intact. Splice does so destructively.

Let's explore exactly how each one works.

## .slice()
Slice is an operator that works on arrays in Javascript. ( and also strings! because they behave like arrays! )

Slice can take in 1 or 2 arguments.

### One Argument

If you pass in one argument, that argument will act as an index. The function will return the portion of the array that remains when starting at the index passed in.

![image of slice code with one argument](https://i.imgur.com/d2KQnrr.png)

Throughout all this, **arr** will remain unaffected.

### Two Arguments

If you pass in two arguments, the first argument acts just like in the previous example. The second argument will also act as an index. The returned array will stop before reaching the index that is equal to the second argument.

![image of slice code with two arguments](https://i.imgur.com/Aec4mHV.png)


## .splice()

Splice works similarly, but will act destructively on the array.

Splice takes in 1 or more arguments.

### One Argument

Splice will return everything from the passed  in index  onward, while deleting it from the array.

![image of splice code with one argument](https://i.imgur.com/T3nwZBy.png)

### Two Arguments

Splice will return everything between the index equalling first argument and the index equalling second argument. It will also delete those same values from the array.

![image of splice code with two arguments](https://i.imgur.com/GNuLhe1.png)

### Three or More Arguments

Splice will use the first two arguments exactly as it did in the Two Arguments case. However, it will also add in any further arguments to the beginning of the array.

![image of splice code with three or more arguments](https://i.imgur.com/FRqhwN7.png)




Thanks for reading! Have a blessed day.

#### - Peter Stone
Jan 17, 2019
