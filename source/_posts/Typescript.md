---
title: Typescript
date: 2024-11-25 04:26:41
tags: Typescript
categories: programming

---

## Object

### interface

``` Typescript
interface NewInterface {
    s : string;
    n : number;
}
```
### type
```Typescript
type newType = {
	s : string;
	n : number;
}
```

## Array
| **property**            | **return**    | **usage**                                         |
| ----------------------- | ------------- | ------------------------------------------------- |
| pop()                   | Array element | get the last element                              |
| includ(target)          | Boolean       | check if the array have a element match target    |
| every((item)=>statment) | boolean       | check if every element match the statement inside |
| join(separator?)        | string        | combine all string into one string with separator |
| \[...array\]            |               | (spread) fill content of the array                |
## Opeartor

### ??

Operator `??` is similar to `||`,
it take the right hand side if left hand side is undefined or null.

Difference:
`??` → use RHS when LHS is `null` or `undefined`
`||` → use RHS when LHS is `null` or `undefined` or `False` or `0`