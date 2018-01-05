---
category: programming
tags:
  - Rust
---

# futures-rs
zero cost abstruction of state machine

# futures-await
Async/await syntax for Rust and the `futures` crate

## abstract

#### async tag
make it returns future instead of result
```
#[async] // tagged with #[async] option
fn fetch(c: Client) -> Result<T> {
  let res = await!()?; // Optional
  if !res.status().is_success() { // Err }

}
```

#### async_stream tag
stream instead of future
```
#[async_stream(item=T)]
for s in T {
  ...
  stream_yield!(await!(..))
}
```

#### await macro
`await!` macro allows blocking the procedure until completion, not blocking the thread

`await!` behaves like a function returns `Result(e)`


the brief procedure of `await!` macro.
```
macro_rules! await {
  let mut future = $e
  loop {
    match poll(&mut future) {
      Ok(Ready(e)) => break Ok(e),
      Ok(NotReady) => {}, // continue and wait
      Err(e) => Err(e)
    }
  }
  // block until NotReady -> Ready(e)
  yield futures::Async::NotReady
}
```

#### asymc_block macro
it doesn't need a dedicated function like `#[async]`, (it's a monad like `thread::spawn()` so can be run with `core.run(Fn(async_block!))`)

here's the brief procedure of it
```
#[proc_macro]
fn async_block(i: TokenStream) -> TokenStream {
  // input -> TokenTree -> TokenStream -> parse -> TokenStream
  let input = TokenStream::from(TokenTree {...,
    // parse input as token node
    ..., kind: TokenNode::Group(Delimiter::Brace, i)})

  let expr = syn::parse(input)

  // token construction..
  token.into() // return Stream
}
```

## nightly features
- [generators](https://github.com/rust-lang/rust/issues/43122)
- [proc_macro](https://github.com/rust-lang/rust/issues/35896)
- [conservative_impl_trait](https://github.com/rust-lang/rust/issues/42183)

