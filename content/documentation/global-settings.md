---
title: "Global settings"
permalink: "/documentation/global-settings/"
layout: page
parent: "Documentation"
---
To change a global setting use .set command as defined below:

```
.set <variable> <value>
```

For example:

```
.set auth-time 1m
```

There are 5 types of values:

* boolean
* integer
* percentage
* time
* enum

A boolean value can be expressed in binary notation (0 and 1) or using the strings ON and OFF. For example:

```
.set public-away 0
```  

IS EQUIVALENT TO  

```
.set public-away OFF
```

A time value can be expressed as integer (the number of seconds) or using the time notation (w=week, d=day, h=hour, m=minute, s=seconds). For example:

```
.set auth-time 300
```

IS EQUIVALENT TO  

```
.set auth-time 5m
```
 
A enum value can be expressed by few predefined constants (see the table below). Other types don't need to be explained.

To see the current settings just type .set without arguments.

The table below describes all settings with respective type and acceptable values:

|Variable|Type  |Values|Description|
|--------|------|------|-----------|
|ask-for-op-delay|	time| 	<1s - 60s\>	     |after this time bot asks for op if he wasn't opped before   |
|auth-time	|time|	< 15s - 6m >	    |all unauthorised connections are closed after this time|
|away-time	|time|	< 1m - Infinity >	|bots will stay away for this time|
|bIe-mode-bounce-time	 |time|	< 0s - Infinity >	 |after this time bots will remove b/e/I channel modes  |
|backup-mode-delay	|time |	< 0s - 60s >	   |(to be filled)  |
|between-msg-delay	|time |	< 10s - Infinity >	 |delay time between sending messages when bots are not away (anti-idle)|
|chat-time	|time|	< 60s - Infinity >	 |bots will stay not away for this time|
|clone-life-time	|time|	< 0s - Infinity >	 |time after witch clones are deleted from clone list|
|conn-timeout	|time|	< 16s - 10m \>	  |time after witch all authorsied inacive connection are being closed|
|critical-bots	|integer|	< 0 - Infinity >	 |description     |
|cycle-delay	|time	|< 0s - 60s >   |	time after the bots will enter channel after a part in a cycle     |
|dont-trust-ops	|enum|	<0 \| 1 \| 2\>	|0 : disabled<br>1 : ops (that dont have +f) can op only users that have +s or bots<br>2 : ops (that dont have +f) can op only users that have +s|
|get-op-check	|boolean	| <ON \| OFF\>	|description|
|host-clones	|integer|	<0 - Infinity>  |	number of same-host process to be recognized as clones |
|hub-conn-delay	|time| <10s - 1h>	 |description        |
|ident-clones	|integer| <0 - Infinity>     |	number of same-ident process to be recognized as clones    |
|irc-conn-delay	|time|	<10s - 1h>  |	description       |
|keep-nick-check-delay	|time	<5s - 1d>    |	time after bots will check for nick availability|
|max-matches	|integer|	<0 - Infinity> |	description    |
|ops-per-mode|	enum|	<0 \| 1 \| 2 \| 3>|	number of ops in one line when there are enemies in the channel|
|perip-burst-size	 |integer|	< 1 - Infinity>  |	description |
|perip-burst-time	 |time|	< 0s - Infinity> |	description    |
|perip-ignore-time	|time|	< 0s - Infinity> |	description    |
|perip-max-shown-conns	|integer	|< 0 - Infinity> |	description|
|pre-0.2.11-final-compat	|boolean|	< ON  \| OFF >	    |description|
|pre-0.2.3-final-compat	|boolean|	< ON\  \| OFF >	    |description|
|private-ctcp	|boolean|	< ON \| OFF >	|description|
|proxy-clones	|integer	|< 0 - Infinity\>	  |description    |
|public-away	|boolean|< ON  \| OFF \>	|description|
|quarantine-time	|time| < 0s - 2m >	|description       |
|randomness	 |percentage	|< 0% - 100%\>	   |description|
|rejoin-delay|	time| < 0s - 60s >	  |description |
|rejoin-fail-delay |	time	 |< 7s - 60s >	  |description|
|remember-old-keys |	boolean|	< ON \| OFF > |	description  |
|synflood-ignore-time|	time|	< 0s - Infinity >	 |description|
|synflood-max-conns|	integer|	< 1 - Infinity >  |description|
|telnet-owners	|enum|	< 0 \| 1 \| 2\>	|0 : owners are not allowed to connect via telnet<br>1 : all owners having +pt flags can connect to main via telnet<br>2 : only owners having +pt flags set and having their ip added to host list are allowed to connect|
|wasop-cache-time	 |time|	< 0s - Infinity >	|description   |
