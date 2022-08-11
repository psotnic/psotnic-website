---
title: "Config file"
permalink: "/documentation/config-file/"
layout: page
parent: "Documentation"
---
Each instance of running irc bot needs a separate configuration file. There are three types of bots

* Main (also known as hub)
* Slave
* Leaf

Depending on the content of the configuration file psotnic will act as the main bot, slave or as a leaf.

### Mandatory options for all bots:

|option|description|
|------|-----------|
|nick  |	bot's nickname (eg. fido)|
|realname|	bot's real name (eg. Dog in the fog)|
|nickappend|	list of characters that will be appended to nick if it is taken (eg. -\|`^, this setting is taken in consideration only if altuidnick is set to 0)|
|myipv4|	ip address of the bot (eg. 88.45.56.15, 0.0.0.0 means any address)|

### Mandatory options for main (aka hub)

|option|description|
|------|-----------|
|listen|port on which main is listening for connections from slaves and owners (eg. 12345)|
|ownerpass|	md5 sum of owner password for partyline, you will be asked for this password each time you connect to the partyline, in order to generate the password run ./psotnic -p and copy the obtained md5 sum to the config file|

### Additional options for main

|option|description|
|------|-----------|
|ssl_listen|	SSL secured port for partyline access, to connect use openssl s_client command (man s_client).|

### Mandatory options for slave

|option|description|
|------|-----------|
|listen|	port on which slave is listening for connections from leafes (eg. 12345)|
|hub|	ip, port, pass of the main bot (eg. 123.123.123.123 9000 some_password)|

### Mandatory options for leafs

|option|description|
|------|-----------|
|hub	|ip, port, pass and slave handle name (eg. 111.111.111.111 8000 some_password slave1)|

### Additional options for leafs

|option|description|
|------|-----------|
|alt	|ip, port of alternative slave (eg. 1111.111.222.222 9000, it can be set more than once)|

### Additional options for all bots

|option|description|
|------|-----------|
|ident |bot's username (default: same as account name)
|handle|bot's handle that is visible in the partyline (default: same as nick)
|vhost |ipv4 or ipv6 address (e.g: 217.2.3.54 or 3ffe:2f4:56:35:0:0:0:23), domain names are not supported (default: determined by the operating system)|
|logfile|	file where bot logs some actions (default: /dev/null :)|
|userlist|	userlist (aka. userfile) will be stored there (default: $nick.ul)                                                                                                |
|altuidnick|	turns on/off changing of nick to 0 when nick is taken (by default it is turned ON)|
|ctcptype|ctcp version (default: random).<br>Available options:<br>0 none<br>1 psotnic<br>2 irssi<br>3 epic<br>4 lice<br>5 bitchx<br>6 dzony loker<br>7 luzik<br>8 mirc 6.14|
|keepnick|	keepnick (default: 0)|
|kickreason|	kick reason used for most kicks|
|limitreason	|kick reason used when somebody overrides channel limit|
|keepoutreason|	kick reason for keepout setting|
|partreason	|part reason|
|quitreason	|quit reason|
|cyclereason	|cycle reason|
|bnc	|ip, port, pass of the bnc (only BNC from http://www.gotbnc.com is supported)|
|router|	ip, port, pass of the router (only cisco routers are supported)|

### Additional options for all bots, those options can be set more than once.

|option|description|
|------|------------|
|server|ipv4 (or ipv6 in case of 0.2.3 or newer) address and port of irc server.| Additionally you can add a password, if this is necessary to connect. (eg. 218.234.456.123 6667 password)|
|server6 |ipv6 address and port of the irc server (e.g: 3ffe:2f4:56:35:0:0:0:23 6667)| (this option has been removed in 0.2.3 version)|
|ssl_server|specifies SSL server, syntax is the same as in server option|
