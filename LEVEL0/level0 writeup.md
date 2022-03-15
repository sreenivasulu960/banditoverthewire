# **LEVEL0**
## Challenge
> The goal of the level is to login into the game using ssh .The given details are
> - username=bandit0
> - host/remote address= bandit.labs.overthewire.org
> - port=2220
> - password=bandit0

To login into a remote server we use ssh client let see how to install and connect using the client
<details><summary>On Linux</summary>

### Installation
 open the terminal(Ctrl+Alt+T) and type the below command

```sh
$ sudo apt install openssh-client
```

You can verify the installation by typing the command

```sh
$ ssh -V
```

The output should be something like this, my ssh version is OpenSSH_8
```sh
 OpenSSH_8.2p1 Ubuntu-4ubuntu0.4, OpenSSL 1.1.1f  31 Mar 2020
 ```
 ---------------------------------------------------
### Conncecting
To connect we use ssh command the syntax is  ```ssh username@host``` therefore the command is
 ```sh
 $ ssh bandit0@bandit.labs.overthewire.org
 ```

To mention port we can use -p flag
 ```
 $ ssh bandit0@bandit.labs.overthewire.org -p 2220
 ```

Thats it now we can use this command to login to the server lets do it
```sh
root@kali:~# ssh bandit0@bandit.labs.overthewire.org -p 2220
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([176.9.9.172]:2220)' can't be established.
ED25519 key fingerprint is SHA256:xOMImN4lodtNUxc+8pieveXo7KEdBMztFjgmIcfdVmk.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])?

```
when u are connecting for the first time it will ask you are you sure you want to continue type yes and click enter then it asks for the password.Type bandit0
and press enter after that u will be in bandit server
```sh
root@kali:~# ssh bandit0@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org\'s password:
Linux bandit.otw.local 5.4.8 x86_64 GNU/Linux

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to Steven or morla on
irc.overthewire.org.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ and /proc/ is disabled
  so that users can not snoop on eachother. Files and directories with
  easily guessable or short names will be periodically deleted!

  Please play nice:

    * don\'t leave orphan processes running
    * don\'t leave exploit-files laying around
    * don\'t annoy other players
    * don\'t post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few usefull tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /usr/local/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /usr/local/pwndbg/
    * peda (https://github.com/longld/peda.git) in /usr/local/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /usr/local/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)
    * checksec.sh (http://www.trapkit.de/tools/checksec.html) in /usr/local/bin/checksec.sh

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us through IRC on
  irc.overthewire.org #wargames.

  Enjoy your stay!

bandit0@bandit:~$

```
If you see the prompt ```bandit0@bandit``` so login is successfull

**Note:**
> You may get the error connection closed dont worry run the command again
-----------------------------------------------------
## Adding user to ssh_config file(Optional)
for logging in we have to use the whole command every time like
```sh
 root@kali:~ # ssh bandit0@bandit.labs.overthewire.org -p 2220
```
instead of that we can create our custom hostname and login using it .open config file located at  ~/.ssh/config  using a editor(u can use vi or nano or gedit)
```sh
root@kali:~# (gedit/vi/nano) ~/.ssh/config
```
Now add the below block of text to the files
```
Host bandit*
  Hostname bandit.labs.overthewire.working
  User bandit0
  Port 2220
```
now u can simply run the below command instead of whole command
```sh
root@kali:~# ssh bandit0
```
when u run the above command it matches the bandit0
with bandit*(means all the strings starting with bandit) since they match it will use the details mentioned(User,Port ..etc) to login

For more information see [level0.pdf](https://github.com/sreenivasulu960/banditoverthewire/blob/main/LEVEL0/banditlevel0.pdf)
