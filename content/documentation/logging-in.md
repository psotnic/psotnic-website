---
title: "Logging in"
permalink: "/documentation/logging-in/"
layout: page
parent: "Documentation"
---
There are 3 ways to login into the botnet:

* Telnet
* DCC
* SSL

## Telnet
Telnet mode consists to connect to the hub through a client that supports telnet protocol like Putty, Penguinet, SecureCRT, and obviously Telnet (free and available in any platform). For example:

```
telnet box1.shellprovider.com 31337
```

Oh Oh! Got an empty screen? Don't care, it is normal! Before to see any signs of life by the hub you have to type the ownerpassword then, if correct, you will see the login request. Too hard for you? Then you might consider to use a dedicated client like Psotnic Client and EaZy Psotnic.

## DCC
DCC (Direct Client Connection) mode consists to connect to the hub through a DCC Chat using your preferred IRC Client (Kvirc, Xchat, mIRC, etc). For example:

```
/DCC chat hubnickname
```

If you can't host a DCC session because you are firewalled or behind a NAT (eg: router) you can start a passive DCC by asking the hub to host a session for you using the chat command. For example:

```
/msg hubnickname chat
```
You will see a DCC chat request from the hub bot. Doesn't it work? Make sure you have inserted a correct IP in the myipv4 directive in the config file.

## SSL
SSL connection works in a similar way as telnet connection, with the exception that all transfered data is being encrypted.

In order to connect to hub you have to use some kind of SSL-enabled client. In the example bellow I present use ssl client from openssl ulity:

```
openssl s_client -connect box1.shellprovider.com:12345
```

**NOTE**: You can only connect to hub which has ssl_listen port open. Any SSL connections directed to ordinary listen port (the one used for telnet) will FAIL.

After connection has been established, you have to supply ownerpassword (as with telnet connection bot won't ask you for it, you just have to type it in), username and password.
