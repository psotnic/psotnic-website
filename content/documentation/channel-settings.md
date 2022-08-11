---
title: "Channel settings"
permalink: "/documentation/channel-settings/"
layout: page
parent: "Documentation"
---
To change a channel setting use .chset command as defined below:

```
.chset <channel> [variable] [value]
```

For example:

```
.chset #psotnic aop-bots 2
```

These settings can also used to make a default configuration with .dset command: .dset variable value The default configuration will be loaded each time you join (or add) a new channel. For example:

```
.dset aop-bots 2
```

Also you can use .gset command to apply a single set to all channels:

```
.gset [variable] [value]
```

For example:

```
.gset aop-bots 2
```

List of all available settings with respective type and acceptable values:
<br>

|Variable|Type  |Values|Description|
|--------|------|------|-----------|
|aop-bots|	time|	< 0 - Infinity>|	number of bots assigned to oping joining +ao ppl|
|bitch|	boolean|	< ON \| OFF >	|turns on/off bitch mode|
|bot-aop-bots|	time|	< 0 - Infinity>|number of bots assigned to oping joining bots|
|bot-aop-mode|	time	|            < 0 - Infinity>|	it sets bot autop op mode, when it is set to 2, bots op like in < 0.2.7 versions (fast but insecurity - if someone pretends to be a bot, he migh get oped), when it is set to 1, bots use getop code to gain op only if the number of ppl to kick is not larger then 4, otherwise they use < 0.2.7 op code, when this setting is set to 0, bots will only use get op code (it might be useful when you really care that nobody would spoof bots hosts, but you also do not care whether bots op fast or slow). Additionally when takeover is enabled, bots will always use the fastest op mode (that is 0).|
|channel-ctcp|	time|	< 0 - Infinity>|	description|
|check-shit-on-nick-change|time|	< 0 - Infinity>|	description
|clonecheck|boolean|	< ON \| OFF >|	clone protection
|dynamic-bans|boolean|	< ON \| OFF >	turn ON in order to make that the bots remove the |bans from the bans list after a specific time. If set OFF the bots will not remove the bans automatically
|dynamic-exempts	|boolean|	< ON - OFF >	like above but for the exempts
|dynamic-invites|	boolean|	< ON - OFF >	like above but for the invites
|enforce-bans|	boolean|	< ON \| OFF >	turns on/off ban enforcing (=kicking ppl that are |matching placed ban)
|enforce-limits|	boolean|	< ON \| OFF >|	turns on/off limit enforcing, if somebody with +n flag places lower limit then the number of users bots will `remove' surplus
|getop-bots|	integer|	< 0 - Infinity >	|number of bots which bot will ask for op
|guardian-bots|	percentage|	< 0 - 100 >|	number of bots which will guard channel modes
|idiots	|integer|	< 0 - 5 >|0 off<br>1 remove +a only (if exists)<br>2 remove +a and the highest level flag. if user will have no flag we'll give him +d<br>3 remove all flags for 1st offence. 2nd time +d<br>4 +d locally<br>5 +d globally and clear flags for all other channels|
|invite-on-unban-request|	time	|< 0 - Infinity>|	description|
|invite_bots	|integer	|< 0 - Infinity>|	number of bots witch bot will ask for invitation|
|keepout|	boolean|	< ON \| OFF >|	when enabled, channel will be kept locked (+i), all not added (not having +v or +o) ppl will be forced to leave :P|
|limit	|boolean|	< ON \| OFF >	|turns on/off autolimit feature|
|limit-bots|	integer|	< 0 - Infinity>|	number of limit bots assigned to autolimiting|
|limit-offset|	integer|	< 0 - Infinity>|	autolimit offset (new limit := number_of_users + this value)|
|limit-time	|time|	< 0 - Infinity>|	autolimit recheck time|
|limit-time-down	|time	|< 0 - Infinity>|	description|
|limit-time-up	|time	|< 0 - Infinity>	|description|
|limit-tolerance	|integer	|< 0 - Infinity>	|tolerance of the limit (:= limit offset this value), this setting prevents too frequent changes of the limit|
|lockdown|	boolean|	< ON \| OFF >|	turns on/off locking of the channel if the number of bots on the channel reaches critical level
|lockdown-time|	time|	< 0 - Infinity>|	not used ;-)|
|owner-limit-time|	time	|< 0 - Infinity>|	description|
|protect-chmodes	|time	|< 0 - Infinity>|	can protect/forbid channel modes. example: "+nt-ims" will make sure that 'n' and 't' are always set, and that 'i' 'm' and 's' are not set.|
|punish-bots|	time|	< 0 - Infinity>|	number of bots assigned to kicking ppl that are doing sth nasty|
|stop-nethack|	boolean|	< ON / OFF >|	turns on/off kicking of -f ppl upon receiving op from the irc serve|
|strict-bans	|time	|< 0 - Infinity>	|description|
|takeover|	boolean|	< ON \| OFF >|	turns on/off takeover mode|
|user-exempts	|enum|	< 0 \| 1 \| 2 >|0 every op can set +/-e<br>1 only owners (+n), bots and servers can set +/-e<br>2 only exempts added by partyline can be in the list|
|user-invites	|enum	|< 0 \| 1 \| 2 >|	like above|
|user-reops	|enum|	< 0 \| 1 \| 2 >|	like above|
|wasoptest|boolean|< ON \| OFF >|When it's set ON the op list is "stored" by the bot/s that split during a net-split and when this bot/s returns from the split it check if the op list is the same and kick all user/s that have been oped during the split.|
