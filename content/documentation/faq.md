---
title: "Frequently asked questions"
permalink: "/document/faq/"
layout: page
parent: "Documentation"
---
**Q**: What's new in x.y.z version?<br>
**A**: See changelog.<br>
  
**Q**: Do i have to put slaves and/or main on irc?<br>
**A**: No.<br>

**Q**: My bots do not want to connect to irc server, but i can connect to irc via other irc clients, what did i do wrong?<br>
**A**: First of all double check corectness of the vhost you have typed in, second make sure that ip is present in the system (you could be nated), if ip is not present put 0.0.0.0 as your ip :).<br>

**Q**: Why does my bot not join any channels?<br>
**A**: Try adding hostmask to the bot's handle. psotnic bots do not join channels if their hostmask is not added into their handle. Type ".list i" on partyline to see if a hostmask is added or not.<br>

**Q**: Why do bots place ban on *!*@*.siol.net (or simillar)?<br>
**A**: This ban results from proxy clone protection, bots ban given isp when they detect that number of ppl having identless connection exceeds value of .set proxy-clones, if you do not want to ban given isp, simply add a new user, give him +c channel flags and add hosts witch you would like to exclude from clone protection, if you want to completely turn off that kind of protection simply set proxy-clones to 0.<br>

**Q**: Whats the difference between static and non staic version?<br>
**A**: Static version includes all system libraries needed to start the bot in itself, contrary to non static version witch is has library dependensies. Furthermore non static (=dynamic) binary provides dynamic module loading interface witch allows you to load custom pieces of code.<br>

**Q**: I get following error: `[!] Invalid packet: 62 Barklays BanjaLuka 27 #celjani`, what should i do?<br>
**A**: Unlink slave to which `Barklays' is connected to.<br>

**Q**: How to add psotnic to cron?<br>
**A**: Just run `./psotnic -a conf1 conf2 conf3' and so on.<br>

**Q**: Why do i get `Lost 123.123.123.123 / 12345 (Leaf123: not a slave)` error on the partyline?<br>
**A**: Because you have told your leaf to connect to main bot instead of the slave bot.<br>

**Q**: Main's userlist is broken, can i do about it?<br>
**A**: Login into any slave's account, change your slave's config in such a way to make it main bot (simple removal of hub line should do the trick), then start the slave. You should notice that your slave has just become main bot :). Log into new main and .export userlist, then send exported file to your real main's account and setup new main from the scrach, then login into it and .import userfile witch you have just uploaded. Please note that all .info and .shit expiration information will be lost !!!<br>

**Q**: How to part a bots from a channel containing `strange' caracters in its name?<br>
**A**: Type .channels, get the number of channel that interests you (start counting from 1 :P), type .mpart <number of channel>.<br>

**Q**: How to add bot with dynamic ip?<br>
**A**: Simply set myipv4, vhost and bot's address to 0.0.0.0, additionaly you can give your bot `p' flag which will allow bot to update its temporary host everytime it gets connected to irc.<br>

**Q**: Will there ever be a version for windows?<br>
**A**: You have the source, get cygwin and compile it for yourself.<br>

**Q**: How to remove 'x' user?<br>
**A**: .export userfile, edit it (remove 'x' flag), .import edited userlist and remove the user :)<br>
