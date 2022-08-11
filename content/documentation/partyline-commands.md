---
title: "Partyline commands"
permalink: "/partyline-commands/"
layout: page
parent: "Documentation"
---
To run a partyline command just type "." before it otherwise, it will be recognized as a chat line.

For example:

```
.help
```

Command argument semantics Mandatory arguments are written in < > tags, if you do not supply the argument command will fail. For example:

```
.info <handle>
```

Options that are not mandatory are written in [ ] tags, if you omit those options default value will be taken. For example:

```
.bots [expr] [flags]
```

There is additional construct that looks like [%TEXT], where % is a character that has to be put before the parameter, otherwise command will fail (or it will work differently than expected). The reason of such construct is that some commands take two optional parameters, and the prefixed character is the only way to distinguish between them.

For example:

```
.+exempt [#chan] [%time] <mask> [reason]
```

## List of all available commands

|      |       |     |
|------|-------|-----|
|      |       |     |
|+bot  |	<handle\> <ip\>      |	Adds new bot with name handle and with adress ip     |
|+chan |	<chan\> [key]	 |Adds new channel with name chan and optionally sets key     |
|+exempt|	[#chan] [%time] <mask\> [reason]  |	Adds ban exception to the chan for given mask for time|
|+host |	<handle\> <host\>    |	Adds a host to a specific handle    |
|+info |	<handle\> <key\> <value\>   |	Description   |
|+invite	|[#chan] [%time] <mask\> [reason]  |	Like "+exempt" but for invites         |
|+reop |	[#chan] [%time] <mask\> [reason] |	Like "+exempt" but for reops    |
|+shit |	[#chan] [%time] <mask\> [reason] |	Adds a shit to the chan for a given mask for a specific time|
|+stick |	[#chan] [%time] <mask\> [reason]  |	Like above but for skick bans  |
|+user |	<handle\> [host]     |	Adds a user specifying a handle and a host  |
|-bot  |	<handle\>  |	Removes a bot specifying the handle           |
|-exempt	|<mask\> [chan]      |	Removes an exepmt specifying the mask and the chan   |
|-host |	<handle\> <host\>    |	Removes a host of a handle          |
|-info |	<handle\> <key\>     |	Description   |
|-invite	|<mask\> [chan]      |	Like "-exempt" but for invites      |
|-reop |	<mask\> [chan] |	Like "-exempt" but for reops              |
|-shit |	<mask\> [chan] |	Removes a shit specifying the mask and the chan    |
|-user |	<handle\>  |	Removes a user specifying the handle          |
|abuse ||	Description|
|boot |	<handle\> <reason\>   |	Description   |
|bots |	[expr] [flags]	Description   |
|bottree|	|Shows the bottree |
|bye	 |[reason]|	To exit from partyline giving a "reason of exit"   |
|chaddr|	<handle\> <ip\>|	Description  |
|channels|	|Shows all channels where are the bots    |
|chattr|	<handle\> <flags\> [chan]	 |Sets the flag/s for a specific handle for a chan|
|chhandle|	<handle\> <handle\>	 |renames handle|
|chnick|	<bot\> <nick\>	|Changes the nick of a specific bot         |
|chpass|	<handle\> <pass\>	   |Changes the password of a specific handle  |
|chset |	<chan\> [var] [value]  |	Changes a setting of a specific channel |
|clearoffences|	[handle]|	Clear all the offences of a handle        |
|cwho |	<bot\> <chan\> [flags]|	Description   |
|downbots|	|Shows the bots that are down |
|exempts	|[chan]	   |Shows the exempt/s of a channel|
|export|	<file\> [pass]	|Export the userlist  |
|gset |	[var] [value]	|Changes a specific setting for all the channels|
|import|	<file\> [pass]	|Import a userlist|
|info |	<handle\>	  |Shows info of a specific handle|
|invites|	[chan]    |	Shows the invite/s of a channel|
|list |	<apcdsvuiU\> [bot]	   |Description    |
|match |	<expr\> [flags] [chan]	|Description  |
|mcycle|	<chan\>	   |Parts and joins the bots on a specific channel |
|mjoin |	<chan\> [key] [delay]  |	To join all bots on a specific channel with a key  |
|mk|	<o\|n\|a\> <chan\> [lock]	|To make a mass kick (o=ops, n=non ops, a=all)|
|mpart|	<chan\>	    |To part all bots from a specific channel       |
|names|	<bot\> <chan\>	 |Description   |
|offences|	[handle]	|Shows the offences of a specific handle        |
|owners|	|Shows the owners   |
|rcycle|	<bot\> <chan\> |	Like "mcycle" but for one bot                   |
|rdie |	<bot\>	|Kills one bot|
|reops|	[chan]	|Shows the reop/s of a specific channel   |
|restart|	<bot\>	   |Restart a specific bot   |
|rflags|	<handle\> <chan\>    |	Description   |
|rjoin|	<bot\> <chan\> [key]	   |Like "mjoin" but for one bot       |
|rjump|	<bot\> <host\> [port]   |	Jumps a bot on a host giving a port     |
|rjump6|	<bot\> <host\> [port]  |	Like rjump but for Ipv6|
|rjumps5|<bot\> <proxy\> <port\> <server\> <port\>|	Description     |
|rpart|	<bot\> <chan\>  |	Like "mpart" but for one bot|
|save ||	Saves userlist|
|set|	[var] [value] |	Sets a setting   |
|shits|	[chan] |	Shows the shits of a channel |
|sjoin|	<slave\> <chan\> [key]|	Like "mjoin" but for a specific slave and his leafs  |
|spart|	<slave\> <chan\>	|Like "mpart" but for a specific slave and his leafs|
|status|	[bot] |	Description  |
|tkmjoin	|<chan\> [key] [delay]	|Join all bots on a channel with takeover mode sets ON|
|tkrjoin|	<bot\> <chan\>	|Join one bot on a channel with takeover mode sets ON|
|tksjoin|	<slave\> <chan\> [key]	|Join a slave and his leafs on a channel with takeover mode sets ON|
|upbots|	|Description   |
|update|	<bot\> [URL]   |	To update a bot giving the url |
|users|	|Shows all users added|
|verify|	|Description   |
|who	 ||Description|
|whob||	Description|
|whois|	<handle\>|	Shows all the information (flags, hosts etc) of a handle   |
|whom |	|Description|

