---
title: trait Sized<T>
category: programming
tags:
  - Rust
---

fat pointerとなる場合
- slice
- str(slice)
- `Fn(A) -> A` のようなtrait object

またこれらの値へのポインタは16byteになる.
最初の8byteには通常のポインタ同様のデータの先頭番地
続く8byteには
- &[i32]の場合、スライスの要素数
- &str の場合、バイト数
- &Read の場合、`vtable`へのポインタ

