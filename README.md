题目来自 [type-challenges](https://github.com/type-challenges/type-challenges)

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
