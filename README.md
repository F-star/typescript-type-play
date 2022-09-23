题目来自 [type-challenges](https://github.com/type-challenges/type-challenges)

常用的判断相等的 Equal，类型体操中不时会用到。

```ts
type Equal<X, Y> = (<T>() => T extends X ? 1 : 2) extends <T>() => T extends Y ? 1 : 2 ? true : false
```

### [14. First of Array](https://github.com/type-challenges/type-challenges/blob/main/questions/00014-easy-first/README.md)

取出 数组/元组的 第一个类型。

```ts
type First<T extends any[]> =
  T extends [infer First, ...unknown[]]
    ? First
    : never

type First2<T extends any[]> = T["length"] extends 0 ? never : T[0]
```

### [898. Includes](https://github.com/type-challenges/type-challenges/blob/main/questions/00898-easy-includes/README.md)

判断 数组 中是否有某个类型，有返回 true，否则为 false。

```ts
type Includes<T extends readonly any[], U> =
  T extends [infer First, ...infer Rest]
    ? Equal<U, First> extends true
      ? true
      : Includes<Rest, U>
    : false
```
