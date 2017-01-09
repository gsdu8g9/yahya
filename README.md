# Welcome to Yahya
--------------------
SSH from terminal even with NATED firewall

## Introduction
------------
Yahya is a tool for encapsulating SSH through HTTP proxies, but
...you might find another use for it. Like for reverse SSH or backdoor :) 

PS: I am not responsible in any way to the use of this tool

Yahya has been compiled on :
 * HPUX 
 * Solaris
 * FreeBSD
 * OpenBSD
 * Linux
 * Win32 (with Cygwin)

Yahya has been tested with the following HTTP proxies :
 * Gauntlet
 * CacheFlow
 * JunkBuster
 * Apache mod_proxy
 * But it works for other files also

Please email me if you get it working on other proxies or compile
it elsewhere.

## How Do I Build It?
------------------
Download zip file https://github.com/zeeshanali/yahya/archive/master.zip
unzip it 
In the yahya directory type '**./configure**' then '**make**'.  Check
out the INSTALL file for more information.


## How Do I Install It?
--------------------
In the yahya directory type '**make install**'.


## How Is It Used?
---------------
Setting up yahya with SSH/OpenSSH is very simple.  Adding
the following line to your **~/.ssh/config** file will usually do
the trick (replace proxy.example.com and 8080 with correct values):

**ProxyCommand /usr/local/bin/yahya proxy.example.com 8080 %h %p**

NOTE: Command line syntax has changed since version 1.5.  Please
notice that the proxy port is NOT optional anymore and is required
in the command line.


## How Do I Use The HTTP Authentication Feature?
---------------------------------------------
You will need to create a file that contains your usename and password
in the form of :
username:password

I suggest you place this file in your **~/.ssh** directory.

After creating this file you will need to ensure that the proper perms
are set so nobody else can get your username and password by reading
this file.  So do this :
chmod 600 myauth

Now you will have to change the ProxyCommand line in your ~/.ssh/config
file.  Here's an example :

**ProxyCommand /usr/local/bin/yahya proxy.work.com 80 %h %p ~/.ssh/myauth**

The proxy authentication feature is very new and has not been tested
extensively so your mileage may vary.  If you encounter any problems
when trying to use this feature please email me.  It would be helpful
if you could include the following information :
- Proxy version (ie. Gauntlet Proxy, Microsoft Proxy Server, etc)
- Operating system you are trying to run yahya on
- Command line syntax you are using
- Any error messages that are visible to you

*NOTE: I have had problems using the auth features with Mircosoft Proxy
 server.  The problems are sporadic, and I believe that they are related
 to the round-robin setup that I was testing it again.  Your mileage may
 vary.

Courtesy
---------
The initial work is done by Agroman -
URL   : http://www.agroman.net/
