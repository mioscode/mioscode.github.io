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
```
$ curl https://sh.rustup.rs -sSf | sh -s -- --no-modify-path
```
--no-modify-path    Don't configure the PATH environment variable
[https://stackoverflow.com/questions/45899815/could-not-write-to-bash-profile-when-installing-rust-on-macos-sierra](https://stackoverflow.com/questions/45899815/could-not-write-to-bash-profile-when-installing-rust-on-macos-sierra)

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

# Reference
[https://www.rust-lang.org/tools/](https://www.rust-lang.org/tools/install)
[https://doc.rust-lang.org/book/title-page.html](https://doc.rust-lang.org/book/title-page.html)
[http://sarojaba.github.io/rust-doc-korean/doc/tutorial.html](http://sarojaba.github.io/rust-doc-korean/doc/tutorial.html)
