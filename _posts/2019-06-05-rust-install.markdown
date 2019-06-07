---
title: "Rust 설치, Hello World"
categories:
  -  Rust
tags:
  - Rust
comments: true
---

# 1. Rustup 설치
rustup: a command line tool for managing Rust versions and associated tools
[https://www.rust-lang.org/tools/](https://www.rust-lang.org/tools/install)

(macOS)

```
$ curl https://sh.rustup.rs -sSf | sh
```

## 1.1. Error
```
1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
>1

error: could not write rcfile file: '/Users/somi.han/.profile'
info: caused by: Permission denied (os error 13)
```
## 1.2. Solution
[https://stackoverflow.com/questions/45899815/could-not-write-to-bash-profile-when-installing-rust-on-macos-sierra](https://stackoverflow.com/questions/45899815/could-not-write-to-bash-profile-when-installing-rust-on-macos-sierra)
```
$ curl https://sh.rustup.rs -sSf | sh -s -- --no-modify-path
```
--no-modify-path    Don't configure the PATH environment variable

```
Welcome to Rust!

This will download and install the official compiler for the Rust programming
language, and its package manager, Cargo.

It will add the cargo, rustc, rustup and other commands to Cargo's bin
directory, located at:

  /Users/somi.han/.cargo/bin

This path needs to be in your PATH environment variable, but will not be added
automatically.

You can uninstall at any time with rustup self uninstall and these changes will
be reverted.

....

Rust is installed now. Great!

To get started you need Cargo's bin directory ($HOME/.cargo/bin) in your PATH
environment variable.

To configure your current shell run source $HOME/.cargo/env
```
터미널을 다시 시작하는 대신 Rust를 바로 사용하려면 쉘에서 다음 명령을 실행하여 시스템 PATH에 수동으로 Rust를 추가
```
$ source $HOME/.cargo/env
```

# 2. Hello World
## 2.1. 프로젝트 생성
```
$ cargo new (프로젝트 이름) --bin
```
프로젝트 이름으로 된 폴더가 생기며, 안에 Rust의 Hello, world를 출력하는 코드파일과 cargo 프로젝트 속성 파일이 생김
## 2.2. 컴파일
```
$ cargo run
```

# 3. Rust nightly install
[https://github.com/rust-lang/rustup.rs/blob/master/README.md#working-with-nightly-rust](https://github.com/rust-lang/rustup.rs/blob/master/README.md#working-with-nightly-rust)

## 3.1. toolchain 설치
```
$ rustup toolchain install nightly
info: syncing channel updates for 'nightly-x86_64-apple-darwin'
376.4 KiB / 376.4 KiB (100 %) 188.2 KiB/s in  2s ETA:  0s
info: latest update on 2019-06-07, rust version 1.37.0-nightly (5eeb567a2 2019-06-06)
info: downloading component 'rustc'
 81.9 MiB /  81.9 MiB (100 %)  11.2 MiB/s in  8s ETA:  0s
info: downloading component 'rust-std'
 56.1 MiB /  56.1 MiB (100 %)   9.8 MiB/s in  5s ETA:  0s
info: downloading component 'cargo'
info: downloading component 'rust-docs'
 11.2 MiB /  11.2 MiB (100 %)   9.5 MiB/s in  1s ETA:  0s
info: installing component 'rustc'
 81.9 MiB /  81.9 MiB (100 %)  12.5 MiB/s in  6s ETA:  0s
info: installing component 'rust-std'
 56.1 MiB /  56.1 MiB (100 %)  14.7 MiB/s in  3s ETA:  0s
info: installing component 'cargo'
info: installing component 'rust-docs'
 11.2 MiB /  11.2 MiB (100 %)   2.1 MiB/s in  5s ETA:  0s

  nightly-x86_64-apple-darwin installed - rustc 1.37.0-nightly (5eeb567a2 2019-06-06)
```

## 3.2. 테스트 실행
```
$ rustup run nightly rustc --version
rustc 1.37.0-nightly (5eeb567a2 2019-06-06)
```

## 3.3. nightly로 디폴트 변경
```
$ rustup default nightly
info: using existing install for 'nightly-x86_64-apple-darwin'
info: default toolchain set to 'nightly-x86_64-apple-darwin'

  nightly-x86_64-apple-darwin unchanged - rustc 1.37.0-nightly (5eeb567a2 2019-06-06)
```


# Reference
[https://www.rust-lang.org/tools/](https://www.rust-lang.org/tools/install)
[https://doc.rust-lang.org/book/title-page.html](https://doc.rust-lang.org/book/title-page.html)
[http://sarojaba.github.io/rust-doc-korean/doc/tutorial.html](http://sarojaba.github.io/rust-doc-korean/doc/tutorial.html)
[https://github.com/rust-lang/rustup.rs/blob/master/README.md#working-with-nightly-rust](https://github.com/rust-lang/rustup.rs/blob/master/README.md#working-with-nightly-rust)