---
title: "Compiling"
permalink: "/documentation/compiling/"
layout: page
parent: "Documentation"
---
## Requirements for compiling
* GNU make
* gcc and g++, both are part of the GNU Compiler Collection
* perl, the Practical Extraction and Report Language
* GNU awk
* Linux, BSD, UNIX-like OSes or Cygwin (MS Windows)
 
## Optional stuff
* Subversion, the source version control system
* OpenSSL with development files
If you are interested in compiling psotnic on openwrt please read on this.

## Compiling
1\. Login into your shell and check if you have the requirements installed 2. Download the source from the psotnic project page on sourceforge or psotnic.com using wget

```
wget http://www.psotnic.com/src/psotnic-0.2.14.tar.gz
```

or checkout psotnic SVN repository and proceed to step 4

```
svn co https://psotnic.svn.sourceforge.net/svnroot/psotnic psotnic
```

2\. Extract the archive

```
tar xzf psotnic-0.2.14.tar.gz
```

3\. Enter into the directory

```
cd psotnic-0.2.14
```

4\. Run configure script

```
./configure
```

5\. If you don't need modules then compile it as static else as dynamic (for debugging use debug):

```
make dynamic
```

6\. Enter into bin directory and check for psotnic executable

```
cd bin
./psotnic -v
```

7\. You will get something like that:

```
Psotnic C++ edition, version current-2007/07/05-ipv6 (Aug 18 2007 13:32:31)
Copyright (C) 2003-2007 Grzegorz Rusin <grusin@gmail.com>
```

8\. Done here, proceed to Config file

There's also a video available that shows how compiling psotnic works.

## configure options
While the above part was a simple and fast way to compile the standard bot, you may want to customize it a bit. This can be done by passing some extra options to the configure script:

|   a              |  b                                                                                     |
|------------------|----------------------------------------------------------------------------------------|
| --with-antiptrace|  Enables ptrace protection - currently not completly implemented and thus not working. |
|--no-irc-backtrace|	|Disables the generation of irc backtraces if the bot crashes.                         |
|--little-endian|	Forces little endianess,
|--big-endian|	Forces big endianess.
|--cc-prefix|	Specify a prefix for the compiler binary.
|--cc-options|	Passes extra options to the compiler.
|--ld-options|	Passes extra options to the linker.
|--disable-adns|	Disables the asynchronous DNS resolver.
|--with-ssl|	Enables the use of ssl encrypted connections. Also see the Warning below the table.
|--with-firedns |Enabled the optional FireDNS asynchronous DNS resolver.<br><br>Warning: When using --with-ssl, you have to provide a "ssl_listen <port>" line in the config file. Otherwise, the bot will run into an endless loop and has to be killed manually.|


## Extra targets
The makefile has some extra targets. Those are:

* debug
* static
* apidox

The debug target compiles psotnic with extra debugging support. if you start it with the -d option, then it won't go to background, but instead will print out everything to the terminal.

If you don't want to load modules, then you can build it with the static target. This way, you'll get a version that is not able to load modules.

The last target, apidox, is used to compile the API documentation. To do this, you need a recent version of doxygen. After running this target, you'll find a new folder "html" in the docs subfolder, which contains the documentation ready for viewing in your favourite browser.
