# Krypton

###level 0
```
$ echo S1JZUFRPTklTR1JFQVQ= | base64 -d
$ ssh krypton1@krypton.labs.overthewire.org
...
$ (echo -e "{wechall credential}"; cat) | nc 176.28.31.8 4141
```

###level 0 -> level 1
```
$ cd /krypton/krypton1/
$ cat README
...
```
[ROT13](https://en.wikipedia.org/wiki/ROT13)

```
$ cat krypton2
YRIRY GJB CNFFJBEQ EBGGRA
$ echo YRIRY GJB CNFFJBEQ EBGGRA | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
LEVEL TWO PASSWORD {password}
$ ssh krypton2@krypton.labs.overthewire.org
...
$ (echo -e "{wechall credential}"; cat) | nc 176.28.31.8 4141
```

###level 1 -> level 2
```
$ cd /krypton/krypton2/
$ cat README
...
$ cat krypton3
OMQEMDUEQMEK
$ mktemp -d
/tmp/tmp.ep2R56MTHW
$ cd /tmp/tmp.ep2R56MTHW
$ ln -s /krypton/krypton2/keyfile.dat
$ ls -al
...
lrwxrwxrwx 1 krypton2 krypton2      29 Jan 17 16:34 keyfile.dat -> /krypton/krypton2/keyfile.dat
$ chmod 777 .
$ /krypton/krypton2/encrypt /etc/issue
$ cat ciphertext
GNGZFGXFEZX
$ cat /etc/issue
Ubuntu 14.04.5 LTS \n \l
$ /krypton/krypton2/encrypt A
failed to open plaintext
$ echo AAAAAAAAAA > plain
$ /krypton/krypton2/encrypt ./plain
$ cat ciphertext
MMMMMMMMMM
$ echo "AA AA" > ./plain; /krypton/krypton2/encrypt ./plain; cat ciphertext
MMMM
$ echo "aA" > ./plain; /krypton/krypton2/encrypt ./plain; cat ciphertext
MM
$ echo {a..z} > ./plain; /krypton/krypton2/encrypt ./plain; cat ciphertext
MNOPQRSTUVWXYZABCDEFGHIJKL
$ echo OMQEMDUEQMEK | tr '[MNOPQRSTUVWXYZABCDEFGHIJKL]' '[A-Z]'
{password}
$ ssh krypton2@krypton.labs.overthewire.org
...
$ (echo -e "{wechall credential}"; cat) | nc 176.28.31.8 4141
```


