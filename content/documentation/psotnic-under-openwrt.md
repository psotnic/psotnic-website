---
title: "psotnic under openwrt"
permalink: "/psotnic-under-openwrt/"
layout: page
parent: "Documentation"
---
The compilation process of psotnic for embedded systems is a little bit more difficult than the one for ordinary linux box.

In order to compile it you must have following prerequisites:

psotnic source code with revison at least 64 (previous versions didn't have support of embedded systems)
build environment for linux distribution installed on the router:
openwrt whiterussian 0.9
(TODO: fill with more links to build enviroments)
While the first one is obvious, the second is usually not. The reason for having build environment (sometimes called build root) is the fact that the linux distribution running on the router has different set of system libraries and that the router is not an x86 compatible machine, so code compiled on your linux box won't be understood by the router. Here comes the build environment with set of libraries and development tools (compilers, linkers, ...) that allow you to build software that will be working on your router.

Bellow I will present compilation process for my Linksys WRT54GL router. It has OpenWRT whiterussian 0.9 installed.

1. Unpack OpenWrt-SDK-Linux-i686-1.tar.bz2 to your home directory:<br>
```
tar xzf OpenWrt-SDK-Linux-i686-1.tar.bz2
```

2. Unpack psotnic-current.tar.gz to your home directory:<br>
```
tar xzf psotnic-current.tar.gz
```

3. Enter psotnic directory<br>
```
cd psotnic-current
```

4. Run ./configure script<br>
```
./configure --cc-prefix=~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc- --little-endian --cc-options="-fno-builtin -nostdinc++ -nodefaultlibs -Os" --ld-options="-luClibc++ -lm" --disable-adns
```
<br>
If you are interested in explanation of this line, read below.

5. Compile
```
make dynamic
```

This should cause bot to compile. If you get problems with compilation, please form a bug report. Make sure that you give us information about the router (linux distro and model should be enough) and linux box you are compiling on.

The output binary should be about 600KB.

As for now I do not recommend compiling in debug mode, because the binary will be around 3MB. If you are having problems, and you insist on using debug version, please make sure that you strip debug symbols out of it, to do use strip utility from your build environment:
```
~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc-strip bin/psotnic
```

6. Copy bin/psotnic to your router. That's all!!!
<hr>
Below there is an explanation of configure parameters for:

```
./configure --cc-prefix=~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc- --little-endian --cc-options="-fno-builtin -nostdinc++ -nodefaultlibs -Os" --ld-options="-luClibc++ -lm" --disable-adns
```

1. --cc-prefix

```
--cc-prefix=~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc-
```

This option tells configure script use different compiler than the default, in this case instead of using g++, compiler from build environment will be used.

Each call to a compiler will be prefixed with `~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc-`, so in our case `~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc-g++` will be called. Which of course exists in the system:
```
grusin@it:~$ ls -al ~/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc-g++
-rwxr-xr-x 1 grusin grusin 281819 2007-01-30 17:43 /home/grusin/OpenWrt-SDK-Linux-i686-1/staging_dir_mipsel/bin/mipsel-linux-uclibc-g++
```
and points to a compiler from the build environment.

NOTE: Each build environment will probably require different cc_prefix.

2. --little-endian, --big-endian<br>
```
--little-endian
```
<br>
This options tells configure script to configure cryptographic support for machine with little endian processor.

NOTE: You should check what kind of endian does CPU in your router have, in case of having router with big endian CPU pass --big-endian instead of --little-endian.

3. --cc-options<br>
```
--cc-options="-fno-builtin -nostdinc++ -nodefaultlibs -Os"
```
<br>
This line forces passing `-fno-builtin -nostdinc++ -nodefaultlibs -Os` compile options to the compiler.

NOTE: You should check what compiler options are needed for building software for your router's linux distribution. In case of openwrt, those should work :)

4. --ld-options<br>
```
--ld-options="-luClibc++ -lm"
```
<br>
This line forces linker to link with micro c++ library and math library.

NOTE: You should check what linker options are needed.

5. --disable-adns<br>
```
--disable-adns
```
<br>
This options forces configure script to disable asynchronous dns support. If you do not pass this option bot will be built with adns support and it will require libpthread to be instilled on your router. It is advised to disable this option, because adns support consumes a lot of memory.
