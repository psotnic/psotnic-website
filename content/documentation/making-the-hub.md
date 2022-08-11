---
title: "Making the hub"
permalink: "/documentation/making-the-hub/"
layout: page
parent: "Documentation"
---
The first step to make your botnet is the creation of the main bot (aka hub).

Choosing a main password (ownerpass):

Now, enter into the directory where you compiled the bot (eg: bin ) and create the MD5 hash of your main password using the following command:

```
echo "yourpassword" | ./psotnic -p
```

For example:

```
echo "b0tm4st3r" | ./psotnic -p
```

You will have an output like this:
```
Psotnic C++ edition, version current-2007/07/05-ipv6 (Aug  5 2007 23:27:43)
Copyright (C) 2003-2007 Grzegorz Rusin <grusin@gmail.com>


Bot is now running in MD5 hash generator mode
Warning: strings longer than 100 characters will be cut
 
string to hash: MD5 hash      : aa21ad108a57d28b87b8b4c05bceec57
```
Take note of the MD5 hash (aa21ad108a57d28b87b8b4c05bceec57) , we will need it later.


Creating the configuration file: Create a new text file with your preferred editor (eg: pico). For example:

```
pico conf.apocalypse
```

According to config file directives fill the requested informations and paste the ownerpass saved before:

For example:
```
nick            apocalypse
realname        Time of Judgment
nickappend      _`
myipv4          0.0.0.0
listen          31070
ownerpass       aa21ad108a57d28b87b8b4c05bceec57
 
ident           knight
handle          apocalypse
 
server          195.40.6.37 6667
server          212.40.5.89 6668
```

Save the file and proceed to encryption using the following command: ./psotnic -c <filename>

For example:
```
./psotnic -c conf.apocalypse
```

Move <filename>.dec (decrypted config file) to safe place if you do not want others to see your configuration.

Starting the main bot (Hub): To start a bot just use ./psotnic <configfile> For example:
```
./psotnic conf.apocalypse
```

The bot will request you to supply an username (handle) and a password (userpassword) through IRCNet therefore open your IRC client and set it with: /msg <botnickname> mainowner <username> <password>

For example:
```
/msg apocalypse mainowner mafiaboy 1l0v3p1zz4
```
Note: The userpassword is NOT the ownerpassword and must be at least 8 characters long.

A message ("Account created") will inform you that all is done.
