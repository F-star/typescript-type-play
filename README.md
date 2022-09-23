
### [First of Array](https://github.com/type-challenges/type-challenges/blob/main/questions/00014-easy-first/README.md)

取出 数组/元组的 第一个类型。

```ts
type First<T extends any[]> =
  T extends [infer First, ...unknown[]]
    ? First
    : never

type First2<T extends any[]> = T["length"] extends 0 ? never : T[0]
```

