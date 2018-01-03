---
title: tips of writing OS/Kernel
category: program
tags:
  - OS
  - Kernel
  - GRUB
---

# Tips of writing OS/Kernel

## asm

| name |  mnemonic   |syntax|compiler|
|:----:|:-----------:|:----:|:------:|
| nasm |mov dest src | Intel| nasm   |
| GAS  |mov src %dest| AT&T |GNU Assembler/as| 

AT&T:
 - add `$` for imm, `pushl $4`
 - add `%` for reg, `mov $4 %eax`

## Links

#### tutorials
- [Build yourself a Linux](https://github.com/MichielDerhaeg/build-linux)
- [Writing an OS in Rust](https://os.phil-opp.com/)

#### asm
- [GAS/NASM](https://www.ibm.com/developerworks/jp/linux/library/l-gas-nasm.html)

#### BootLoader
- [GRUBで簡単なOSカーネルを動かしてみる](http://inaz2.hatenablog.com/entry/2015/12/31/221319)
- [なぜx86ではMBRが"0x7c00"にロードされるのか](https://www.glamenv-septzen.net/view/614)
- [MBRの構造](http://caspar.hazymoon.jp/OpenBSD/arch/i386/stand/mbr/mbr_structure.html)

#### toolchains
- [xargo](https://github.com/japaric/xargo)
  - sysroot manager, build my `std`
 
#### OS in Rust

- [rustboot](https://github.com/charliesome/rustboot)
- [puddle](https://github.com/jvns/puddle)
- [rust_os](https://github.com/thepowersgang/rust_os)
- [sos-kernel](https://github.com/hawkw/sos-kernel)
- [SnowFlake](https://github.com/SnowFlakeOS/SnowFlake)
- [Redox](https://github.com/redox-os/redox)
