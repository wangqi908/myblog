---
title: macOS汇编学习日志（零）：配置
date: 2020-03-03 23:00:00
tags: 
 - 学习笔记
 - 汇编
categories:
 - 学习笔记
toc: true
thumbnail: https://pic.imgdb.cn/item/5e5e28a998271cb2b8346f93.jpg
---

**As**se**m**bly

<!--more-->

图 / 明日方舟

</br>


## 0 配置：安装nasm

先把运行环境调好。来用`nasm -v`看下NASM版本。

```
$ nasm -v
nasm: error: unable to find utility "nasm", not a developer tool or in PATH
```

按照几个参考链接的说法，macOS里自带的nasm版本很老，功能受限，因此需要自行升级。

然而这台Mac里根本没有自带nasm，那就用brew安装。

```bash
$ brew install nasm gdb
==> Downloading https://homebrew.bintray.com/bottles/nasm-2.14.02.mojave.bottle.
==> Downloading from https://akamai.bintray.com/77/77a183895137e0f95d897d3339923
# 静候安装完成
```

安装过程的尾声，我看到这样一些提示：

```
gdb requires special privileges to access Mach ports.
You will need to codesign the binary. For instructions, see:
  https://sourceware.org/gdb/wiki/BuildingOnDarwin

On 10.12 (Sierra) or later with SIP, you need to run this:
  echo "set startup-with-shell off" >> ~/.gdbinit
```

“gdb需要特权以访问Mach Ports ... 在 OS 10.12 及以上带SIP的，需要运行 ...”

由于后者在我的Mac系统版本中有对应，那么就按照提示输入`echo "set startup-with-shell off" >> ~/.gdbinit`，前者先无视了。

```bash
$ echo "set startup-with-shell off" >> ~/.gdbinit
$ nasm -v
NASM version 2.14.02 compiled on Dec 27 2018
# 确认一下nasm是否安装成功以及查看版本
```

查看一下该版本nasm支持的格式：

```
$ nasm -hf
  * bin       flat-form binary files (e.g. DOS .COM, .SYS)
    ith       Intel hex
    srec      Motorola S-records
    aout      Linux a.out object files
    aoutb     NetBSD/FreeBSD a.out object files
    coff      COFF (i386) object files (e.g. DJGPP for DOS)
    elf32     ELF32 (i386) object files (e.g. Linux)
    elf64     ELF64 (x86_64) object files (e.g. Linux)
    elfx32    ELFX32 (x86_64) object files (e.g. Linux)
    as86      Linux as86 (bin86 version 0.3) object files
    obj       MS-DOS 16-bit/32-bit OMF object files
    win32     Microsoft Win32 (i386) object files
    win64     Microsoft Win64 (x86-64) object files
    rdf       Relocatable Dynamic Object File Format v2.0
    ieee      IEEE-695 (LADsoft variant) object file format
    macho32   NeXTstep/OpenStep/Rhapsody/Darwin/MacOS X (i386) object files
    macho64   NeXTstep/OpenStep/Rhapsody/Darwin/MacOS X (x86_64) object files
    dbg       Trace of all info passed to output stage
    elf       ELF (short name for ELF32)
    macho     MACHO (short name for MACHO32)
    win       WIN (short name for WIN32)
```

舒服了。

那么至此，安装步骤就完成了。

</br>

## 1 测试

下面创建helloworld.asm文件：（参考了各种链接找到的可靠代码，我还什么都不会，只是为了测试nasm是否正常工作）

```x86asm
section .data
    ;(数据段)放置变量
    ;字符串常量
    string DB 'Hello World!'
    ;字符串长度，$表示string_len的偏移地址-string的偏移地址，就是string长度
    string_len DB $ - string

section .bss
    ;bss段（也是存放变量，不过不知道与data有何区别）

section .text
    ;(代码段)放置代码

;定义入口函数
global _MAIN

_MAIN:
	;rax、rdi、rsi、rdx分别存放系统调用号、类型(输出)、字符串地址、字符串长度
    MOV rax,0x2000004
    MOV rdi,1
    MOV rsi,string
    MOV rdx,string_len
    syscall
    ;退出，rax、rdi分别存放系统调用号、类型(退出)
    mov rax,0x2000001
    mov rdi,0
    syscall
```

然后进行汇编与运行。

```bash
$ nasm -f macho64 -o helloworld.o helloworld.asm
# 汇编
$ ld -macosx_version_min 10.14 -o helloworld -e _MAIN helloworld.o -lSystem
# 链接动态库
$ ./helloworld 
# 运行helloworld
Hello World!
            __mh_execute_header!MAIN%??- 4
                                            _MAIN__mh_execute_headerdyld_stub_binderstringstring_len% 
```

万事俱备，接下来就可以进入汇编语言以及nasm的正式学习阶段了。

</br>

> 参考：
>
> [Evian Zhang's naive blog](https://evian-zhang.github.io/)
>
> [简书 @redexpress 「macOS环境汇编语言教程（一）：环境搭建」](https://www.jianshu.com/p/552f37d3c9b0?from=timeline&isappinstalled=0)
>
> [CSDN @_well_s 「如何在MacOS上玩儿汇编?」](https://blog.csdn.net/u011987514/article/details/72615406)
>
> [灰信网 MAC通过HOMEBREW安装NASM（MAC上的汇编环境，附常见错误解决办法）](http://www.freesion.com/article/1082238258/)