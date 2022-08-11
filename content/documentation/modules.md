---
title: "Modules"
permalink: "/documentation/modules"
layout: page
parent: "Documentation"
---
Psotnic, if compiled as dynamic, can load C++ modules. A module is a piece of code that implements some additional features (eg: antispam, antiflood, voicelikeop..) which can be loaded by one (or more) Psotnic bot.

## Compiling a module
There are two ways of compiling modules: Using the makefile: After running configure, you will find a Makefile in the modules directory. If you are in that directory, you can simply run "make" and all modules will be compiled. Also, you can run make with the name of the module you want as target. If you want for example to compile vctrl:

```
make vctrl
```

However, if you want to compile your own modules or third-party modules, you'll have to use the second method: Compiling by hand: Once you extracted the Psotnic source archive you will find modules in the modules directory. You can compile a module using the following command: g++ -o <modulename>.so <modulename>.cpp -shared For example:

```
cd modules
g++ -o vctrl.so vctrl.cpp -shared
```

This will compile the voice control module (aka voicelikeop).

## Loading a module
To load a module you have to use the load directive in the config file as defined below:

```
load /path/to/module.so
```

For example:
```
load /home/jack70/psotnic-0.2.14/modules/vctrl.so
```

This is NOT a partyline command! If you want to load modules via partyline, read the Botnet Control document in advanced techniques section. Each bot can load more than one module, but overcharging a single bot with many modules is not a good idea.

Note: Each module is protected by md5 sum, which is stored in the config file, as soon as the bot loads the module for the first time. If you alter the module file (vctrl.so in this example), the bot will refuse the load the module. This is to prevent authorized code from being injected into the bot.

If you are a module developer you probably would like to have the ability of changing the module without the need of recreating the config file. In that case you should use debugLoad directive instead of load.

```
debugLoad /home/jack70/psotnic-0.2.14/modules/vctrl.so
```

## List of all available modules
These modules are beeing shipped with the official tarballs:
<br>

|Module|Author|Description|
|------|------|-----------|
|control|	Grzegorz Rusin <pks@irc.pl>|	?|
|date|	cgod <c@sii.ath.cx>|	Gets actual date in current timezone (!date); in GMT (!gdate); current date, time, day of week numerically (!ddate); and also can compute day of week from given date (!day <yyy-mm-dd>)
|log|	Stuart Scott <stu@wilf.co.uk>|	Logging module producting eggdrop-format logfiles.|
|noautorejoin|	patrick <patrick@psotnic.com>|	Bans users who rejoin automatically after being kicked.|
|op|	Grzegorz Rusin <pks@irc.pl>|	Provides a public !op command to let users op somebody.|
|peak|	matrix <admin@areaunix.org>|	?|
|peak2|	cgod <c@sii.ath.cx>	|Displays last peak (max. number of users) on channel(s), can operate on more channels and can be managed directly from irc; has auto-save also|
|plog|	patrick <patrick@psotnic.com>|	Logging module with per-channel options.
|raw|	patrick <patrick@psotnic.com>|	Lets you send raw data to the IRC server via partyline.|
|repeat|	patrick <patrick@psotnic.com>|	Detects users who repeat or flood and kicks/bans them. It has also a lagcheck.|
|spam|	Grzegorz Rusin <pks@irc.pl>|	?|
|subop|	Stuart Scott <stu@wilf.co.uk>	|?|
|uptime|	patrick <patrick@psotnic.com>|	shows system uptime.|
|vctrl|	patrick <patrick@psotnic.com>|	Gives voiced users the possibility to conrol the channel. Commands are: !kick, !ban, !unban, !voice, !devoice, !topic|
|words|	cgod <c@sii.ath.cx> |	Kicks/bans user who used some words which are in database (ban is based on number of violations); can operate on more channels and can be managed directly from IRC; has auto-save, ignore list, black list, chan list, etc.

## List of deprecated modules
These modules are not part of psotnic anymore for various reasons. If you think you need them, you can find them in older revisions in the svn repository. But be warned: The modules haven't been adapted to the new modules-API, so you have to port them before you can use them.
<br>

|Module|Author|Description|
|------|------|-----------|
|country	|Stuart Scott <stu@wilf.co.uk>|	?|
|explain|	Stuart Scott <stu@wilf.co.uk>|	?|
|google|	matrix <admin@areaunix.org>	? |
|seen|	Stuart Scott <stu@wilf.co.uk>|	?|
|useful|	Stuart Scott <stu@wilf.co.uk>|	?|
