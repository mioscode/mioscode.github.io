---
title: "(Rust) 설치 및 실행 + nightly 버전"
categories:
  -  Rust
tags:
  - Rust
  - nightly
comments: true
---

# Rust 설치
```
$ curl https://sh.rustup.rs -sSf | sh
```

# 설치 확인
```
$ rustc --version
```

# nightly Rust 
## 설치
```
$ rustup toolchain install nightly
info: syncing channel updates for 'nightly-x86_64-apple-darwin'
info: latest update on 2019-07-09, rust version 1.38.0-nightly (78ca1bda3 2019-07-08)
info: downloading component 'rustc'
 58.7 MiB /  58.7 MiB (100 %)   7.7 MiB/s in  7s ETA:  0s
info: downloading component 'rust-std'
168.5 MiB / 168.5 MiB (100 %)   7.9 MiB/s in 21s ETA:  0s
info: downloading component 'cargo'
info: downloading component 'rust-docs'
 11.6 MiB /  11.6 MiB (100 %)   8.7 MiB/s in  1s ETA:  0s
info: installing component 'rustc'
 58.7 MiB /  58.7 MiB (100 %)   9.7 MiB/s in  5s ETA:  0s
info: installing component 'rust-std'
168.5 MiB / 168.5 MiB (100 %)  17.5 MiB/s in  9s ETA:  0s
info: installing component 'cargo'
info: installing component 'rust-docs'
 11.6 MiB /  11.6 MiB (100 %)   1.1 MiB/s in  8s ETA:  0s

  nightly-x86_64-apple-darwin installed - rustc 1.38.0-nightly (78ca1bda3 2019-07-08)

```

## 실행 
```
$ rustup run nightly rustc --version
rustc 1.38.0-nightly (78ca1bda3 2019-07-08)
```

## 디폴트 설정
```
$ rustup default nightly
info: using existing install for 'nightly-x86_64-apple-darwin'
info: default toolchain set to 'nightly-x86_64-apple-darwin'

  nightly-x86_64-apple-darwin unchanged - rustc 1.38.0-nightly (78ca1bda3 2019-07-08)
```

# (참고) 업데이트
```
$ rustup update

```

# Build
```
$ cd <프로젝트 폴더>
$ cargo build --release
    Finished release [optimized] target(s) in 0.30s
```

# Error
## 내용
```
$ cargo build --release
   Compiling rocket v0.4.1
error[E0432]: unresolved import `std::boxed::FnBox`
 --> /Users/somi.han/.cargo/registry/src/github.com-1ecc6299db9ec823/rocket-0.4.1/src/fairing/ad_hoc.rs:2:5
  |
2 | use std::boxed::FnBox;
  |     ^^^^^^^^^^^^^^^^^ no `FnBox` in `boxed`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0432`.
error: Could not compile `rocket`.

To learn more, run the command again with --verbose.
```

## 해결
```
$ cargo --version
cargo 1.37.0-nightly (4c1fa54d1 2019-06-24)
$ cargo update
$ cargo build --release

```

# Reference
<https://www.rust-lang.org/tools/install>

<https://github.com/rust-lang/rustup.rs#working-with-nightly-rust>