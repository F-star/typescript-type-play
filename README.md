类型体操练习。

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

### [3. Omit](https://github.com/type-challenges/type-challenges/blob/main/questions/00003-medium-omit/README.md)

移除对象结构中的一些属性。

```ts
type MyOmit<T extends Record<string, any>, K extends keyof T> = {
  [P in keyof T
    as P extends K ? never : P
  ]: T[P]
}
```

### [8. Readonly 2](https://github.com/type-challenges/type-challenges/blob/main/questions/00008-medium-readonly-2/README.md)

将对象类型中特定的 key 设置为 readonly，第二个参数 T 是可选的，不提供的话，将所有 key 设置为 readonly

```ts
type MyReadonly2<T extends object, K extends keyof T = keyof T> = {
  [P in Exclude<keyof T, K>]: T[P]
} & {
  readonly [P in K]: T[P]
}
```

### [9. Deep Readonly](https://github.com/type-challenges/type-challenges/blob/main/questions/00009-medium-deep-readonly/README.md)

深度 readonly，嵌套的对象的 key 也加上 readonly

```ts
type DeepReadonly<T> = {
  readonly [P in keyof T]: 
    T[P] extends object
      ? T[P] extends Function
        ? T[P]
        : DeepReadonly<T[P]>
      : T[P]
}
```
