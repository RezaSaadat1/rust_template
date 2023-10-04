# Rust Lang Resources
https://www.youtube.com/watch?v=IgC2HvBesms

https://www.youtube.com/watch?v=jB7aJDAvSuo

https://static.rust-lang.org/dist/2023-04-20/


Rust ESP32
https://www.youtube.com/watch?v=0PPPdqoDBQs
https://github.com/esp-rs


https://docs.rust-embedded.org/book/

https://manuel.bernhardt.io/posts/2022-11-04-rust-development-for-the-raspberry-pi-on-apple-silicon/

https://cxx.rs

Docs.rs/

```
# Enable multi-arch
sudo dpkg --add-architecture amd64
# Fix repos
echo 'deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb [arch=amd64,i386] http://security.ubuntu.com/ubuntu jammy-security main restricted universe multiverse

deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports/ jammy main restricted universe multiverse
deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports/ jammy-updates main restricted universe multiverse
deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports/ jammy-backports main restricted universe multiverse
deb [arch=arm64] http://ports.ubuntu.com/ubuntu-ports/ jammy-security main restricted universe multiverse' | sudo tee /etc/apt/sources.list

# Install libraries
sudo apt update
sudo apt install libc6:amd64



```

https://www.docker.com/blog/cross-compiling-rust-code-for-multiple-architectures/

https://doc.rust-lang.org/cargo/reference/workspaces.html
https://doc.rust-lang.org/rust-by-example/

https://doc.rust-lang.org/cargo/index.html

https://sagiegurari.github.io/cargo-make/

https://sagiegurari.github.io/cargo-make/


https://rust-lang.github.io/rustup-components-history/

# installing Rust
`
https://opensource.com/article/22/6/rust-toolchain-rustup

```sh
binutils-arm-linux-gnueabihf
# Pre
sudo apt install g++-7-arm-linux-gnueabihf gcc-7-arm-linux-gnueabihf rust-gdb sshapass
binutils-arm-linux-gnueabihf


 # Rust Installation
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustup target add armv7-unknown-linux-gnueabihf
cargo install cross
cargo install cargo-make

rustup update
rustup show

rustup target list
rustup toolchain list
rustup default stable-x86_64-unknown-linux-gnu

rustup toolchain link my-toolchain /usr/arm-linux-gnueabihf/bin
rustup default my-toolchain

https://github.com/rust-lang/rust-analyzer/issues/11558
glibc err 2.28

v0.3.1170
RUST ANALYZER


debugging tools
rust analyzer
codelldb

```



Build commands for cross compiling

```sh
cargo new hello_world --bin
cd hello_world

 rustdoc README.md

# command to build firmware for host
cargo build --release
cargo build
cargo run



# now for cross compiling
export CC_armv7-unknown-linux-gnueabihf=arm-linux-gnueabihf-gcc
export CXX_armv7-unknown-linux-gnueabihf=arm-linux-gnueabihf-g++
export AR_armv7-unknown-linux-gnueabihf=arm-linux-gnueabihf-ar
export LD_armv7-unknown-linux-gnueabihf=arm-linux-gnueabihf-ld



cargo build --release --target armv7-unknown-linux-gnueabihf --sysroot /usr/arm-linux-gnueabihf
cargo build --target armv7-unknown-linux-gnueabihf
cargo build --target $TARGET --sysroot 




```


Config file for this package looks like
```toml
[package]
name = "rust_firmware"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]


cargo build --release --target
[target.armv7-unknown-linux-gnueabihf]
linker = "arm-linux-gnueabihf-gcc"

https://www.dropbox.com/sh/hkn4lw87zr002fh/AAAO-HxFQzfmmPQQ9KVmoooGa?dl=0


```



Make
```MakeFile

[tasks.build]
script = [
    "cargo build",
    "--target=armv7-unknown-linux-gnueabihf",
]

[tasks.release]
script = [
    "cargo build --release",
    "--target=armv7-unknown-linux-gnueabihf",
]
```
