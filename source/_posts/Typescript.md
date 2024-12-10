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
```
type = newType = {
	s : string;
	n : number;
}
```

## Array
| property | usage                |
| -------- | -------------------- |
| pop      | get the last element |
|          |                      |
## Opeartor

### ??

Operator `??` is similar to `||`,
it take the right hand side if left hand side is undefined or null.

Difference:
`??` → use RHS when LHS is `null` or `undefined`
`||` → use RHS when LHS is `null` or `undefined` or `False` or `0`