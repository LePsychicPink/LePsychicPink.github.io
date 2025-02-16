---
title: Typescript
tags:
  - Typescript
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
| **property**            | **return**    | **usage**                                                                                  |
| ----------------------- | ------------- | ------------------------------------------------------------------------------------------ |
| pop(), shift()          | Array element | pop() and dequeue()                                                                        |
| push(), unshift()       |               | add item to first / last element                                                           |
| includ(target)          | Boolean       | check if the array have a element match target                                             |
| every((item)=>statment) | boolean       | check if every element match the statement inside                                          |
| join(separator?)        | string        | combine all string into one string with separator                                          |
| slice(start?,end?)      | Array         | extract and start to end elements from an array<br>(can use negative to inverse direction) |
| splice(start?,end?)     | Array         | deleting the start to end elements from an array and return the deleted item               |
| \[...array\]            |               | (spread) fill content of the array                                                         |
## Map
```Typescript
const value = 1;
const map : Map<string,number> = new Map<string,number>();
Map.set('key',value);
Map.get('key') //return 1
```

To initialize, can use `Object.entries`
```
const obj = { name: 'Bobby Hadz', country: 'Chile' };
const map1 = new Map<string, string>(Object.entries(obj));

// 👇️ Map(2) { 'name' => 'Bobby Hadz', 'country' => 'Chile' }
console.log(map1);

```
## Operator

### ??

Operator `??` is similar to `||`,
it take the right hand side if left hand side is undefined or null.

Difference:
`??` → use RHS when LHS is `null` or `undefined`
`||` → use RHS when LHS is `null` or `undefined` or `False` or `0`

### keyof
keyof object, used as type
```Typescript
Obj = {
	one: '1',
	two: '2',
	three: '3'
}
```

keyof typeof Obj is equal to 
```Typescript
type A = 'one'|'two'|'three'
```
### typeof
typeof object, used as type

## Promise

### race
```Typescript
  const funcs: Promise<any>[] = [asyncFunction1, asyncFunction2];
  await Promise.race(funcs); // see tither of them resolve first
```