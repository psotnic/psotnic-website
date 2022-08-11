---
title: "User management"
permalink: "/documentation/user-management/"
layout: page
parent: "Documentation"
---
## Adding users
```
.+user batman
```

## Adding host
```
.+host batman BatMan*!*movies@peace.and.love.net
```

## Setting password and flags
```
.chattr batman +k #psotnic
```

## Checking users
```
.whois batman
.clearoffences batman
```

## Removing users
```
.-user batman
```

## List of user flags

|Flag|Description|Privileges|
|----|-----------|---------|	
|x|Main owner	|full control|
|s|Super owner	|d|
|n|Normal owner	|-|
|m|Master	|-|
|f|Friend	|-|
|o|Op	|-|
|v|Voice	|-|
|a|Auto-mode	|-|
|d|Deop	|-|
|q|Quiet	|-|
|k|Kick	|-|
|c|Clone	|-|
|i|Invite	|-|
|r|Reop	|-|
|e|Idiot exempt	|-|
|p|Partyline	|-|

Note: x, s, n, p flags are not allowed to be used as local.
