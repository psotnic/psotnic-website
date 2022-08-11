---
title: "bc command"
permalink: "/documentation/bc-command/"
layout: page
parent: "Documentation"
---
The .bc command (bc stands for Botnet Control) allows main owner (and only main owner) to send direct commands to one of the bots in the botnet.

By default psotnic supports only few commands, additional functionally can be easily extended by module writers.


## Syntax
```
.bc <bot> <command> [arguments]
```

Where bot is the handle of bot you would like to give command to.


## Changing config file
Viewing configuration of given bot:

```
.bc <bot> cfg
```

Example:

```
 [09:35] #pks# bc hub cfg
 cfg: nick ptest
 cfg: realname Psotnic C++ Edition
 cfg: nickappend _-^`|
 cfg: ident grusin
 cfg: oidentd-config
 cfg: handle hub
 cfg: bnc 0.0.0.0 0
 cfg: router 0.0.0.0 0
 cfg: hub 0.0.0.0 0
 cfg: server warszawa.irc.pl 6667
```

The .bc bot cfg command has the same semantics as .chset command, other words it allows to query just one variable

```
 [09:39] #pks# bc hub cfg realname
 cfg: realname Psotnic C++ Edition
```

or to change the value of a variable:

```
 [09:40] #pks# bc hub cfg realname I am proud to be a bot!
 [09:40] #pks# cfg realname I am proud to be a bot!
 cfg: realname has been set to I am proud to be a bot!
```

There are some special variable that can occur several times in the configuration time:

* server
* alt
* ssl_server

In order to alter values of those variables, it is required to prefix them with - (remove) and +(add) character.

To remove irc server warszawa.irc.pl 6667:

```
[10:06] #pks# bc hub cfg -server warszawa.irc.pl 6667
[10:06] #pks# cfg -server 0.0.0.0 0
cfg: removing entry: server warszawa.irc.pl 6667
```

and add krakow.irc.pl 6677:

```
.bc hub cfg +server kwakow.irc.pl 6667
[10:06] #pks# bc hub cfg +server kwakow.irc.pl 6667
[10:06] #pks# cfg +server kwakow.irc.pl 6667
cfg: adding new entry: server kwakow.irc.pl 6667
```

NOTE: Config file changes are not saved until you explicitly save them. In order to save changes do:

```
.bc <bot> cfg-save
```
