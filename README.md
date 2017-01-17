# Krypton

level 0
```
$ echo S1JZUFRPTklTR1JFQVQ= | base64 -d
```

level 0 -> level 1
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
LEVEL TWO PASSWORD ......
$ ssh krypton2@krypton.labs.overthewire.org
...
$ (echo -e "..........................."; cat) | nc 176.28.31.8 4141
...

