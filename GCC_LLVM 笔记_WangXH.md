<h1 style="text-align:center">GCC/LLVM 笔记</h1>

--------------------------------------------------------------------------------
# 1. 安装

## 1.1. LLVM
* 安装
    * windows: 下载 [LLVM-MinGW](https://github.com/mstorsjo/llvm-mingw/releases), 解压, 并设置环境变量 `Path = %llvm-mingw%\bin;`
        * 下载哪个版本? 一般格式为 `llvm-mingw-<版本>-ucrt-x86_64.zip`, 如 `llvm-mingw-20220323-ucrt-x86_64.zip`, 其中
            * `ucrt`: Universal CRT
            * `x86_64`: 64 位版本
* 查看版本
    ```shell
    clang -v
    clang++ -v
    lldb -v
    ```

## 1.2. GCC
* [GCC 官方文档](https://gcc.gnu.org/onlinedocs/)
* 安装
    * windows: 下载 [MinGW-w64](https://github.com/niXman/mingw-builds-binaries/releases), 解压, 并设置环境变量 `Path = %MinGW%\bin;`
        * 下载哪个版本: 一般格式为 `x86_64-<版本>-release-win32-seh-<次版本>.7z`, 如 `x86_64-12.1.0-release-win32-seh-rt_v10-rev3.7z`, 其中
            * `x86_64`: 64 位版本
            * `win32`: windows 平台
            * `seh`: 新版本
* 查看版本
    ```shell
    gcc -v
    g++ -v
    gdb -v
    ```

--------------------------------------------------------------------------------
# 2. 基础

## 2.1. 基本流程
* 流程: $hello.c \xrightarrow{预处理 -E} hello.i \xrightarrow{编译 -S} hello.s \xrightarrow{汇编 -c} hello.o \xrightarrow{链接} hello.exe$
    1. 预处理 (Pre-Processing)
        * 整理代码: 加入头文件, 替换宏变量和宏代码, 删除注释等
        * 如果不指定输出文件, 会打印在命令行
        * 预处理不检查语法错误
    1. 编译 (Compiling)
        * 生成汇编代码
        * 编译阶段只检查函数的声明和调用处是否符合函数原型, 不会检查其他文件中的函数定义
    1. 汇编 (Assembling)
        * 生成机器能识别的二进制机器码
    1. 链接 (Linking)
        * 链接其他 `.o` 文件或链接库
        * 生成程序
* 命令概览
    流程   | 命令                                   | 输出文件
    :----- | :------------------------------------- | :-------
    预处理 | `gcc/clang -E 代码 -o 预处理文件`            | C 代码输出: `.i` </br>C++ 代码输出: `.ii`
    编译   | `gcc/clang -S 预处理文件 -o 编译文件`        | `.s`
    汇编   | `gcc/clang -c 编译文件 -o 汇编文件`          | `.o`
    链接   | `gcc/clang 汇编文件列表 [链接库] -o 程序`    | `.out`, 或 `.exe`
* 也可以直接编译链接成可执行目标文件
    * `gcc/clang 代码列表 [链接库]  -o 目标文件`
> linux 下运行程序: `./程序.out`

## 2.2. 常用选项
选项名          | 作用
:-------------- | :---
`-o`            | 指定目标文件
`-E`            | 仅进行预编译
`-S`            | 生成汇编文件
`-c`            | 只编译不连接, 生成目标文件 `.o`
`-Wall`         | 对源文件的代码有问题的地方发出警告
`-w`            | 不生成任何警告信息
`-I 路径`       | 指定头文件路径, Linux 系统中一般为 `/usr/include`
`-i 文件`       | 指定头文件名字
`-L 路径`       | 指定库文件路径, Linux 系统一般为 `/usr/lib` 和 `/lib`
`-l 库`         | 指定库文件名字
`-g`            | 在目标文件中嵌入调试信息, 以便调试程序
`-O<0|1|2|3>`   | 代码优化等级, `-O0`: 不优化, `-O3`: 最高等级优化

## 2.3. 链接库
* 链接库是预编译的目标文件 (object files) 的集合, 可被链接进程序
* 静态链接库
    * 存档文件 (archive file), 后缀为 `.a`
    * 编译静态链接库
        1. 先生成目标文件 `.o`
        1. 打包 `ar crv [*.a] [*.o]`
    * 调用静态链接库 `gcc -o [*.c] -L [*.a]`
    * 生成可执行目标文件 `gcc -Wall 代码 链接库 -o 可执行目标文件`
    <!-- * 生成静态库: `gcc -static 代码` -->
* 动态链接库 (共享链接库)
    * 使用动态链接库生成的文件通常体积较小, 但运行时依赖库文件
        * 在 Linux 中, 动态链接库的后缀名通常是 `.so`
        * 在 Windows 系统中, 动态链接库的后缀名为 `.dll`
    * 编译动态链接库
        1. 生成位置无关目标代码 `gcc -fPIC -c 源代码列表`
        1. 生成动态链接库 `gcc -shared -o 动态链接库名称 源代码列表或汇编文件列表`
            > 以上两步可以合并为: `gcc -fpic -shared 源文件列表 -o 动态链接库名`
        1. 调用动态链接库生产程序: `gcc -o 程序名 源文件 -L 动态链接库文件列表`

### 2.3.1. windows 下动态链接库实例
* dll 相关代码的编写
    * 头文件: 必要的宏定义和函数声明, 如
        ```c++
        // file: dll.h
        __declspec(dllexport) void fun1(void);
        __declspec(dllexport) void fun2(void);
        ```
    * 程序文件: 定义函数, 如
        ```c++
        // file: dll.c
        #include <stdio.h>
        #include "dll.h"

        __declspec(dllexport) void fun1() {
            printf("This is fun1\n");
        }

        __declspec(dllexport) void fun2() {
            printf("This is fun2\n");
        }
        ```
* 生成 dll
    ```shell
    gcc -shared -o myDll.dll dll.c
    ```
* 使用 dll 的代码的编写
    ```c++
    // main.c
    #include <stdio.h>
    #include "dll.h"

    int main(int argc, char const* argv[]) {
        fun1();
        fun2();
        return 0;
    }
    ```
* 使用 dll 编译
    ```shell
    gcc -o main.exe main.c -L./ myDll.dll
    ```

## 2.4. 属性
* 代码中插入 `__attribute__(属性)`, 或 `__attribute__((属性1, 属性2, [...]))`, 以改变作用对象的特性

### 2.4.1. packed
* `__attribute__((packed))`
    * 压缩, 按字节对齐
* 示例
    ``` C
    struct stu
    {
    　　int a;
    　　char b;
    }__attribute__((packed));
    ```

### 2.4.2. aligned
* `__attribute__((aligned(n)))`
    * 从此之后默认按 n 字节对齐
* 示例
    ``` C
    struct ss
    {
        char a __attribute__((aligned(16)));    // ①
        int b; // __attribute__((aligned(16))); ②
    }; // __attribute__((aligned(16))); ③
    // 结构体字节数: ① 16 ② 32 ③ 8
    ```

### 2.4.3. section
* `__attribute__((section("section_name")))`
    * 将作用的函数或数据放入指定名为 `section_name` 输入段
* 特别注意: `__attribute__` 的 `section` 属性只指定对象的输入段, 它并不能影响所指定对象最终会放在可执行文件的什么段
* 示例
    ``` C
    // 例1
    int var __attribute__((section(".xdata"))) = 0;
    // 例2
    static int __attribute__((section(".xinit"))) functionA(void)
    {
        .....
    }
    ```

### 2.4.4. weak
* `__attribute__((weak))`
    * 指定一个函数是若函数, 消除链接时的 multiple definition

### 2.4.5. 其他...

--------------------------------------------------------------------------------
# 3. 链接脚本
* 将多个目标文件 (`.o`) 和库文件 (`.a`) 链接成一个可执行的文件
* 由一系列命令组成, 每个命令由一个关键字 (一般在其后紧跟相关参数) 或一条对符号的赋值语句组成
* 命令由分号 `;` 分隔开, 文件名或格式名内如果包含分号`;`, 或其他分隔符, 则要用引号 `" ` 将名字全称引用起来, 无法处理含引号的文件名
* `/* ... */`之间的是注释;

## 3.1. 基本结构
通常分为三个部分

* 链接配置 (可有可无)
    * 如一些符号变量的定义、入口地址、输出格式等
        ```c
        STACK_SIZE = 0X200;             // 栈的大小
        OUTPUT_FORMAT(elf32-littlearm)
        OUTPUT_ARCH(arm)
        ENTRY(_start)                   // 程序入口
        ```

* 内存布局定义
    * 脚本中以 `MEMORY` 命令定义了存储空间, 其中以 `ORIGIN` 定义地址空间的起始地址, `LENGTH` 定义地址空间的长度
        ```
        MEMORY
        {
            FLASH (rx) : ORIGIN = 0, LENGTH = 64K
        }
        ```
* 段链接定义
    * 脚本中以 `SECTIONS` 命令定义一些段 (`.text`, `.data`, `.bss`等) 链接分布
        ```
        SECTIONS
        {
            .text :
            {
                *(.text*)
            } > FLASH
        }
        ```
        * `.text` 段即代码段, `*(.text*)` 指示将工程中所有目标文件的 `.text` 段链接到 Flash 中

## 3.2. 常用关键字、命令
* 内存定义命令 `MEMORY`
    ```
    MEMORY {
        NAME1 [(ATTR)] : ORIGIN = ORIGIN1, LENGTH = LEN2
        NAME2 [(ATTR)] : ORIGIN = ORIGIN2, LENGTH = LEN2
        …
    }
    ```
    * `NAME`: 存储区域的名字 (自己可以随意命名)
    * `ATTR`: 定义该存储区域的属性, 可以出现以下 7 个字符:
        ATTR | 含义
        :--: | :---
        `R`  | 只读 section
        `W`  | 读/写 section
        `X`  | 可执行 section
        `A`  | 可分配的 section
        `I`  | 初始化了的 section
        `L`  | 同 `I`
        `!`  | 不满足该字符之后的任何一个属性的 section
    * `ORIGIN`: 关键字, 区域的开始地址, 可简写成 `org` 或 `o`
    * `LENGTH`: 关键字, 区域的大小, 可简写成 `len` 或 `l`
    * 示例
        ```
        MEMORY
        {
        rom (rx) : ORIGIN = 0, LENGTH = 256K
        ram (!rx) : org = 0×40000000, l = 4M
        }
        ```
* 定位符号 `.`
    * 表示当前地址, 它可以被赋值也可以赋值给某个变量
        * 下例是将当前地址赋值给某个变量 (链接器链接是按照 `SECTIONS` 里的段顺序排列的, 前面的排列完之后就能计算出当前地址)
            ```
            RAM_START = .;
            ```
        * 下例是将段存放在特定的地址中
            ```
            SECTIONS
            {
                . = 0×10000;
                .text :
                {
                    *(.text)
                }

                . = 0×8000000;
                .data :
                {
                    *(.data)
                }
            }
            ```
            * `. = 0×10000;` 该语句表示将当前地址设置为 0x10000, 将所有目标文件的 `.text` 段从 0x10000 地址开始存放
* `SECTIONS` 命令
    ```
    SECTIONS
    {
        ...
        secname start BLOCK(align) (NOLOAD) : AT ( ldadr )
        {
            contents
        } >region :phdr =fill
        ...
    }
    ```
    * 这么多参数中, 只有 `secname` 和 `contents` 是必须的, 即可简写成:
        ```
        SECTIONS
        {
            ...
            secname :
            {
                contents
            }
            ...
        }
        ```
    * `secname`: 表示输出文件的段, 即输出文件中有哪些段
    * `contents`: 就是描述输出文件的这个段从哪些文件里抽取而来, 即输入文件, 一般就是目标文件之类的
    * `start`: 表示将某个段强制链接到的地址;
    * `AT(addr)`: 实现存放地址和加载地址不一致的功能, `AT` 表示在文件中存放的位置, 而在内存里呢, 按照普通方式存储
    * `region`: `MEMORY` 命令定义的位置信息
    * 下例: 将目标文件的数据段存放在输出文件的数据段 (段名自己定义, 段名前后必须要有空格)
        ```
        SECTIONS
        {
            ...
            .data :
            {
                main.o (.data)
                *(.data)
            }
            ...
        }
        ```
        * 其中 `*(.data)` 表示将所有的目标的 `.data` 段链接到输出文件 `.data` 段中,
        * 特别注意的是, 之前链接的就不会再链接, 这样做的目的是可以将某些特殊的目标文件链接到地址前面
* `PROVIDE` 关键字
    * 定义一个 (目标文件内被引用但没定义) 符号, 相当于定义一个全局变量, 其他 C 文件可以引用它
        ```
        SECTIONS
        {
            .text :
            {
                *(.text)
                _etext = .;
                PROVIDE(etext = .);
            }
        }
        ```
        * 如上, 目标文件可以引用 `etext` 符号, 其地址为定义为`.text` section 之后的第一个字节的地址
            ``` c
            int main() {
                ...
                extern char _etext; //引用该变量
                ...
            }
            ```
* `KEEP` 关键字
    * 在连接命令行内使用了选项 `–gc-sections` 后, 连接器可能将某些它认为没用的 section 过滤掉, 此时就有必要强制连接器保留一些特定的 section, 可用 `KEEP()` 关键字达此目的
    * 如 `KEEP(* (.text))` 或 `KEEP(SORT(*)(.text))`

## 3.3. 示例
``` c
/*
* In this linker script there is no heap available.
* The stack start at the end of the ram segment.
*/
STACK_SIZE = 0x2000;        /* stack size config 8k */

/*
* Take a look in the "The GNU linker" manual, here you get the following information about the "MEMORY":
*
* "The MEMORY command describes the location and size of blocks of memory in the target."
*/
MEMORY
{
    FLASH_INT     (rx)  : ORIGIN = 0x00000000, LENGTH = 0x00000100
    FLASH_CONFIG  (rx)  : ORIGIN = 0x00000400, LENGTH = 0x00000010
    FLASH_TEXT    (rx)  : ORIGIN = 0x00000410, LENGTH = 0x0001F7F0
    RAM           (rwx) : ORIGIN = 0x1FFFF000, LENGTH = 16K
}

/*
* And the "SECTION" is used for:
*
* "The SECTIONS command tells the linker how to map input sections into output sections, and how to place the output sections in memory.
*/
SECTIONS
{
    /* The startup code goes first into internal flash */
    .interrupts : {
        __VECTOR_TABLE = .;
        . = ALIGN(4);
        KEEP(*(.vectors))       /* Startup code */
        . = ALIGN(4);
    } > FLASH_INT

    .flash_config : {
        . = ALIGN(4);
        KEEP(*(.FlashConfig))   /* Flash Configuration Field (FCF) */
        . = ALIGN(4);
    } > FLASH_CONFIG

    .text : {
        _stext = .;           /* Provide the name for the start of this section */

        *(.text)
        *(.text.*)              /*  cpp namespace function      */
        *(.romrun)              /*  rom中必须的函数             */

        . = ALIGN(4);           /* Align the start of the rodata part */
        *(.rodata)              /*  read-only data (constants)  */
        *(.rodata*)
        *(.glue_7)
        *(.glue_7t)
    } > FLASH_TEXT

    /* section information for simple shell symbols */
    .text : {
        . = ALIGN(4);
        __shellsym_tab_start = .;
        KEEP(*(.shellsymbol))
        __shellsym_tab_end = .;
    } > FLASH_TEXT

    /* .ARM.exidx is sorted, so has to go in its own output section */
    . = ALIGN(4);
    __exidx_start = .;
    PROVIDE(__exidx_start = __exidx_start);
    .ARM.exidx :
    {
        /* __exidx_start = .; */
        *(.ARM.exidx* .gnu.linkonce.armexidx.*)
        /* __exidx_end = .;   */
    } > FLASH_TEXT
    . = ALIGN(4);
    __exidx_end = .;
    PROVIDE(__exidx_end = __exidx_end);

    /* .data 段数据初始化内容放在这里 */
    . = ALIGN(16);
    _etext = . ;
    PROVIDE (etext = .);

    /*
    * The ".data" section is used for initialized data and for functions (.fastrun) which should be copied
    * from flash to ram. This functions will later be executed from ram instead of flash.
    */
    .data : AT (_etext)
    {
        . = ALIGN(4);        /* Align the start of the section */
        _sdata = .;          /* Provide the name for the start of this section */

        *(.data)
        *(.data.*)

        . = ALIGN(4);        /* Align the start of the fastrun part */
        *(.fastrun)
        *(.fastrun.*)

        . = ALIGN(4);        /* Align the end of the section */
    } >

    _edata = .;             /* Provide the name for the end of this section */

    USB_RAM_GAP = DEFINED(__usb_ram_size__) ? __usb_ram_size__ : 0x800;
    /*
        * The ".bss" section is used for uninitialized data.
        * This section will be cleared by the startup code.
        */
    .bss :
    {
        . = ALIGN(4);        /* Align the start of the section */
        _sbss = .;           /* Provide the name for the start of this section */

        *(.bss)
        *(.bss.*)
        . = ALIGN(512);
        USB_RAM_START = .;
        . += USB_RAM_GAP;

        . = ALIGN(4);        /* Align the end of the section */
    } > RAM
    _ebss = .;              /* Provide the name for the end of this section */

    /* 系统堆 */
    . = ALIGN(4);
    PROVIDE (__heap_start__ = .);
    .heap (NOLOAD) :
    {

    } > RAM
    . = ORIGIN(RAM) + LENGTH(RAM) - STACK_SIZE;
    . = ALIGN(4);
    PROVIDE (__heap_end__ = .);

    /*
        * The ".stack" section is our stack.
        * Here this section starts at the end of the ram segment.
        */
    _estack = ORIGIN(RAM) + LENGTH(RAM);

    m_usb_bdt USB_RAM_START (NOLOAD) :
    {
        *(m_usb_bdt)
        USB_RAM_BDT_END = .;
    }

    m_usb_global USB_RAM_BDT_END (NOLOAD) :
    {
        *(m_usb_global)
    }
}

/*** EOF **/
```

--------------------------------------------------------------------------------
# 4. Make
* Make
    * 进行自动编译的程序, 在 makefile 中详细描述用什么工具, 对什么文件, 作何种处理
* makefile
    * 指定了一系列目标 (比如可执行文件) 和依赖 (如对象文件和源文件) 的编译规则, 基本格式如下
        ``` makefile
        目标: 依赖
            命令 # 必须以 TAB 缩进, 不能是空格
        ```
* 工作原理
    ![make工作原理](/assets/make工作原理.png)
* 一个简单的 makefile 文件
    ```makefile
    proc : main.o kbd.o command.o display.o insert.o search.o files.o utils.o
        gcc -o proc main.o kbd.o command.o display.o insert.o search.o files.o utils.o
    main.o : main.c defs.h
        gcc -c main.c
    kbd.o : kbd.c defs.h command.h
        gcc -c kbd.c
    command.o : command.c defs.h command.h
        gcc -c command.c
    display.o : display.c defs.h buffer.h
        gcc -c display.c
    insert.o : insert.c defs.h buffer.h
        gcc -c insert.c
    search.o : search.c defs.h buffer.h
        gcc -c search.c
    files.o : files.c defs.h buffer.h command.h
        gcc -c files.c
    utils.o : utils.c defs.h
        gcc -c utils.c
    clean :
        rm proc main.o kbd.o command.o display.o insert.o search.o files.o utils.o
    ```
    * make 工作机制举例
        * 在当前目录下查找名为 `Makefile/makefile` 的文件
        * 继续找文件中注明的第一个目标文件 (即上文的 `proc`), 并把这个文件作为最终需要生产的目标文件
        * 如果目标文件 (`proc`) 不存在, 或者目标文件后的依赖文件 (`.o`文件) 的修改时间要比目标文件 (`proc`) 新, 那么, 它继续寻找后面定义的命令
        * 如果 `proc` 依赖的 `.o` 文件存在, 那么 make 会在当前文件中寻找目标为 `.o` 文件的依赖性, 若找到则根据规则继续生成一个头文件
        * make会根据文件夹内的 `.c` 或者 `.h` 生成 `.o` 文件, 然后再用 `.o` 文件生成 `proc` 可执行程序
    * 从上面的 Makefile 还可以看到最后一行有一个 `clean` 命令, 但是它没有依赖关系, 只有相关的执行命令, 那么在执行 make 时, 它就不会自动执行, 如果需要执行 `clean`, 则需要指定它的执行: `make clean`
    * 如果该工程已经编译过一次了, 当对其中某个源文件修改后, 只会根据依赖性进行相关文件的重新编译, 而不会整个工程都重新编译
* 使用变量
    * 声明: 独占一行, `变量=值` 的形式
    * 使用: `$(变量)`
    * 示例
        ```makefile
        objects = main.o kbd.o command.o display.o insert.o search.o files.o utils.o
        proc : $(objects)
            gcc -o proc $(objects)
        ```
    * 隐含规则通过 make 变量指定, 比如 `CC` (C 语言编译器) 和 `CFLAGS` (C程序的编译选项)
        * 对于 C++, 其等价的变量是 `CXX` 和 `CXXFLAGS`, 而变量 `CPPFLAGS` 则是编译预处理选项
* 隐晦规则
    * make 可以识别并且自动推导命令, 它识别一个 `.o` 文件, 就会自动将对应的 `.c` 文件加在依赖关系中, 并且也会自动推导出相关的编译命令
    * 示例
        ``` makefile
        objects = main.o kbd.o command.o display.o insert.o search.o files.o utils.o
        proc : $(objects)
            gcc -o proc $(objects)
        main.o : defs.h
        kbd.o : defs.h command.h
        command.o : defs.h command.h
        display.o : defs.h buffer.h
        insert.o : defs.h buffer.h
        search.o : defs.h buffer.h
        files.o : defs.h buffer.h command.h
        utils.o : defs.h
        .PHONY : clean
        clean :
            rm proc $(objects)
        ```
* 伪目标文件
    `.PHONY` 表示 `clean` 是一个伪目标文件

--------------------------------------------------------------------------------
# 5. ELF

## 5.1. 目标对象文件 (Object files)
* 可重定位的对象文件 (Relocatable object file)
    * 由汇编器汇编生成的 `.o` 文件
    * 链接器将一个或多个 `.o` 链接为一个**可执行的对象文件**或者一个**可被共享的对象文件**
    * 可以使用 `ar` 工具将众多的 `.o` 归档成静态链接库文件 `.a` ;
    * 内核可加载模块 `.ko` 文件也是**可重定位的对象文件**
* 可执行的对象文件 (Executable object file)
    * 所谓的 "程序", 如文本编辑器 vi, 调式用的工具 gdb 等
* 可被共享的对象文件 (Shared object file)
    * 动态库文件 `.so`

## 5.2. ELF 文件结构
![elf-文件结构](/assets/elf-文件结构.svg)

* ELF 文件格式的两种不同的视角
    * 在汇编器和链接器看来 ELF 文件是由 Section Header Table 描述的一系列 Section 的集合
    * 执行一个 ELF 文件时, 在加载器 (Loader) 看来它是由 Program Header Table 描述的一系列 Segment 的集合
* ELF Header
    * 描述了体系结构和操作系统等基本信息, 并指出 Section Header Table 和 Program Header Table 在文件中的什么位置
    * 定义
        ```C
        #define EI_NIDENT 16
        typedef struct {
            unsigned char e_ident[EI_NIDENT];   // ELF 的标识信息, 前四位为文件标识, 如 `\x7fELF`, 其他的信息包括文件类型, 数据编码, 大小端等
            ELF32_Half e_type;                  // 目标对象文件的类型
            ELF32_Half e_machine;               // 文件的目标体系架构, 如ARM
            ELF32_Word e_version;               // 0为非法版本, 1为当前版本
            ELF32__Addr e_entry;                // 程序入口的虚拟地址
            ELF32_Off e_phoff;                  // 程序头部表偏移地址
            ELF32_Off e_shoff;                  // 节区头部表偏移地址
            ELF32_Word e_flags;                 // 保存与文件相关的处理器的标志
            ELF32_Half e_ehsize;                // ELF Header 的大小
            ELF32_Half e_phentsize;             // 每个程序头部表的大小
            ELF32_Half e_phnum;                 // 程序头部表的数量
            ELF32_Half e_shentsize;             // 每个节区头部表的大小
            ELF32_Half e_shnum;                 // 节区头部表的数量
            ELF32_Half e_shstrndx;              // 节区字符串表位置
        }Elf32_Ehdr;
        ```
* Program Header Table
    * 保存了所有 Segment 的描述信息
    * 在汇编和链接过程中没有用到, 可有可无
* Section Header Table
    * 保存了所有 Section 的描述信息
    * 在程序加载过程中没有用到, 可有可无
    * 定义
        ```C
        typedef struct{
            Elf32_Word sh_name;       // 节区名, 是节区头部字符串表节区 (Section Header String Table Section) 的索引, 名字是一个 NULL 结尾的字符串
            Elf32_Word sh_type;       // 节区类型
            Elf32_Word sh_flags;      // 节区标志
            Elf32_Addr sh_addr;       // 如果节区将出现在进程的内存映像中, 此成员给出节区的第一个字节应处的位置, 否则为 0
            Elf32_Off sh_offset;      // 节区的第一个字节与文件头之间的偏移
            Elf32_Word sh_size;       // 节区长度
            Elf32_Word sh_link;       // 节区头部表索引链接, 具体解释依赖于节区类型
            Elf32_Word sh_info;       // 附加信息, 具体解释依赖于节区类型
            Elf32_Word sh_addralign;  // 某些节区带有地址对齐约束
            Elf32_Word sh_entsize;    // 某些节区中包含固定大小的项目, 如符号表, 对于这类节区, 此成员给出每个表项的长度字节数
        }Elf32_Shdr;
        ```
        * `sh_type`
            名称         | 取值       | 说明
            :----------: | :--------: | :----
            SHT_NULL     | 0          | 非活动的, 没有对应的节区, 此节区头部中的其他成员取值无意义
            SHT_PROGBITS | 1          | 程序定义的信息, 其格式和含义都由程序来解释
            SHT_SYMTAB   | 2          | 符号表, 目前目标文件对每种类型的节区都只能包含一个, 不过这个限制将来可能发生变化, 一般, SHT_SYMTAB 节区提供用于链接编辑 (指 ld 而言) 的符号, 尽管也可用来实现动态链接
            SHT_STRTAB   | 3          | 字符串表, 目标文件可能包含多个字符串表节区
            SHT_RELA     | 4          | 重定位表项, 其中可能会有补齐内容 (addend) , 例如 32 位目标文件中的 Elf32_Rela 类型, 目标文件可能拥有多个重定位节区
            SHT_HASH     | 5          | 符号哈希表, 所有参与动态链接的目标都必须包含一个符号哈希表, 目前, 一个目标文件只能包含一个哈希表, 不过此限制将来可能会解除
            SHT_DYNAMIC  | 6          | 动态链接的信息, 目前一个目标文件中只能包含一个动态节区, 将来可能会取消这一限制
            SHT_NOTE     | 7          | 以某种方式来标记文件的信息
            SHT_NOBITS   | 8          | 不占用文件中的空间, 其他方面和 SHT_PROGBITS 相似, 尽管此节区不包含任何字节, 成员sh_offset 中还是会包含概念性的文件偏移
            SHT_REL      | 9          | 此节区包含重定位表项, 其中没有补齐 (addends) , 例如 32 位目标文件中的 Elf32_rel 类型, 目标文件中可以拥有多个重定位节区
            SHT_SHLIB    | 10         | 此节区被保留, 不过其语义是未规定的, 包含此类型节区的程序与 ABI 不兼容
            SHT_DYNSYM   | 11         | 作为一个完整的符号表, 它可能包含很多对动态链接而言不必要的符号, 因此, 目标文件也可以包含一个 SHT_DYNSYM 节区, 其中保存动态链接符号的一个最小集合, 以节省空间
            SHT_LOPROC   | 0X70000000 | 这一段 (包括两个边界) , 是保留给处理器专用语义的
            SHT_HIPROC   | OX7FFFFFFF | 这一段 (包括两个边界) , 是保留给处理器专用语义的
            SHT_LOUSER   | 0X80000000 | 此值给出保留给应用程序的索引下界
            SHT_HIUSER   | 0X8FFFFFFF | 此值给出保留给应用程序的索引上界
        * `sh_flag`: 节区是否可以修改, 是否可以执行
            名称          | 取值       | 说明
            :-----------: | :--------: | :----
            SHF_WRITE     | 0x1	       | 节区包含进程执行过程中将可写的数据
            SHF_ALLOC     | 0x2	       | 此节区在进程执行过程中占用内存, 某些控制节区并不出现于目标文件的内存映像中, 对于那些节区, 此位应设置为 0
            SHF_EXECINSTR | 0x4	       | 节区包含可执行的机器指令
            SHF_MASKPROC  | 0xF0000000 | 所有包含于此掩码中的四位都用于处理器专用的语义
        * `sh_link` 和 `sh_info`: 具体含义依赖于sh_type的值
            sh_type     | sh_link       | sh_info
            :---------: | :--------: | :----
            SHT_DYNAMIC | 此节区中条目所用到的字符串表格的节区头部索引  | 0
            SHT_HASH    | 此哈希表所适用的符号表的节区头部索引          | 0
            SHT_REL     | -
            SHT_RELA    | 相关符号表的节区头部索引                      | 重定位所适用的节区的节区头部索引
            SHT_SYMTAB  | -
            SHT_DYNSYM  | 相关联的字符串表的节区头部索引                | 最后一个局部符号 (绑定 STB_LOCAL) 的符号表索引值加一
            其它        | SHN_UNDEF	                                    | 0
* Section
    * 在汇编程序中用 `.section` 声明的 Section 会成为目标文件中的 Section
    * 汇编器还会自动添加一些 Section (比如符号表)
    * 系统预定义的 Section
        section 名 | Section 类型 | 描述
        :--------: | :----------- | :---
        .text      | SHT_PROGBITS | 代码段, 包含程序的可执行指令
        .rodata    | SHT_PROGBITS | 只读数据
        .data      | SHT_PROGBITS | 已经初始化的数据, 将出现在程序的内存映像中
        .bss       | SHT_NOBITS   | 未初始化数据
        .symtab    | SHT_SYMTAB   | 符号表, 包括函数名, 变量名等
        .rel\<name> | SHT_REL      | 包含了重定位信息, 例如 `.text` 节区的重定位节区名字将是: `.rel.text`
        .debug     | SHT_PROGBITS | 此节区包含用于符号调试的信息
        .strtab    | SHT_STRTAB   | 字符串表, 每一个字符串以 `\0` 分隔
        .shstrtab  | SHT_STRTAB   | 存放 section 名的字符串表 (Section Header String Table)
        .got       | SHT_PROGBITS | 全局偏移表, 存储外部符号地址
        .plt       | SHT_PROGBITS | 程序链接表, 存储记录定位信息的额外代码
        .dynsym    | SHT_DYNSYM   | 此节区包含了动态链接符号表
        .comment   | SHT_PROGBITS | 包含版本控制信息
        .eh_frame  | SHT_PROGBITS | 它生成描述如何 unwind 堆栈的表
    * 符号表 `.symtab`
        * 在链接的过程中需要把多个不同的目标文件合并在一起, 不同的目标文件相互之间会引用变量和函数, 在链接过程中, 将函数和变量统称为符号, 函数名和变量名就是符号名
        * 每个定义的符号都有一个相应的值, 叫做符号值(Symbol Value), 对于变量和函数, 符号值就是它们的地址
    * 重定位表 `.relname`
        * 链接器在处理目标文件时需要对目标文件中的某些部位进行重定位, 即代码段和数据中中那些绝对地址引用的位置
        * 对于每个需要重定位的代码段或数据段, 都会有一个相应的重定位表
            * `.rel.text` 是针对 `.text` 的重定位表
            * `.rel.data` 是针对 `.data` 的重定位表
* Segment
    * 在程序运行时加载到内存的具有相同属性的区域, 由一个或多个 Section 组成
        * 比如有两个 Section 都要求加载到内存后可读可写, 就属于同一个 Segment
        * 有些 Section 只对汇编器和链接器有意义, 在运行时用不到, 也不需要加载到内存, 那么就不属于任何 Segment
> 注意: Section Header Table 和 Program Header Table 并不是一定要位于文件开头和结尾的, 其位置由 ELF Header 指出, 上图这么画只是为了清晰
* 注意
    * 目标文件需要链接器做进一步处理, 所以一定有 Section Header Table
    * 可执行文件需要加载运行, 所以一定有 Program Header Table
    * 而共享库既要加载运行, 又要在加载时做动态链接, 所以既有 Section Header Table 又有 Program Header Table
