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

###[TODO] level 1 -> level 2
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

$ ssh krypton3@krypton.labs.overthewire.org
...

$ (echo -e "{wechall credential}"; cat) | nc 176.28.31.8 4141
```

###level 2 -> level 3
```
$ cd /krypton/krypton3/

$ cat README
...

$ cat krypton4
KSVVW BGSJD SVSIS VXBMN YQUUK BNWCU ANMJS 

$ cat HINT1
Some letters are more prevalent in English than others.

$ cat HINT2
"Frequency Analysis" is your friend.
```
[https://inventwithpython.com/hacking/chapter20.html](https://inventwithpython.com/hacking/chapter20.html)
ETAOINSHRDLCUMWFGYPBVKJXQZ
```
$ cat found1
CGZNL YJBEN QYDLQ ZQSUQ NZCYD SNQVU BFGBK GQUQZ QSUQN UZCYD SNJDS UDCXJ ZCYDS NZQSU QNUZB WSBNZ QSUQN UDCXJ CUBGS BXJDS UCTYV SUJQG WTBUJ KCWSV LFGBK GSGZN LYJCB GJSZD GCHMS UCJCU QJLYS BXUMA UJCJM JCBGZ CYDSN CGKDC ZDSQZ DVSJJ SNCGJ DSYVQ CGJSO JCUNS YVQZS WALQV SJJSN UBTSX COSWG MTASN BXYBU CJCBG UWBKG JDSQV YDQAS JXBNS OQTYV SKCJD QUDCX JBXQK BMVWA SNSYV QZSWA LWAKB MVWAS ZBTSS QGWUB BGJDS TSJDB WCUGQ TSWQX JSNRM VCMUZ QSUQN KDBMU SWCJJ BZBTT MGCZQ JSKCJ DDCUE SGSNQ VUJDS SGZNL YJCBG UJSYY SNXBN TSWAL QZQSU QNZCY DSNCU BXJSG CGZBN YBNQJ SWQUY QNJBX TBNSZ BTYVS OUZDS TSUUM ZDQUJ DSICE SGNSZ CYDSN QGWUJ CVVDQ UTBWS NGQYY VCZQJ CBGCG JDSNB JULUJ STQUK CJDQV VUCGE VSQVY DQASJ UMAUJ CJMJC BGZCY DSNUJ DSZQS UQNZC YDSNC USQUC VLANB FSGQG WCGYN QZJCZ SBXXS NUSUU SGJCQ VVLGB ZBTTM GCZQJ CBGUS ZMNCJ LUDQF SUYSQ NSYNB WMZSW TBUJB XDCUF GBKGK BNFAS JKSSG QGWDC USQNV LYVQL UKSNS TQCGV LZBTS WCSUQ GWDCU JBNCS UESGN SUDSN QCUSW JBJDS YSQFB XUBYD CUJCZ QJCBG QGWQN JCUJN LALJD SSGWB XJDSU COJSS GJDZS GJMNL GSOJD SKNBJ STQCG VLJNQ ESWCS UMGJC VQABM JCGZV MWCGE DQTVS JFCGE VSQNQ GWTQZ ASJDZ BGUCW SNSWU BTSBX JDSXC GSUJS OQTYV SUCGJ DSSGE VCUDV QGEMQ ESCGD CUVQU JYDQU SDSKN BJSJN QECZB TSWCS UQVUB FGBKG QUNBT QGZSU QGWZB VVQAB NQJSW KCJDB JDSNY VQLKN CEDJU TQGLB XDCUY VQLUK SNSYM AVCUD SWCGS WCJCB GUBXI QNLCG EHMQV CJLQG WQZZM NQZLW MNCGE DCUVC XSJCT SQGWC GJKBB XDCUX BNTSN JDSQJ NCZQV ZBVVS QEMSU YMAVC UDSWJ DSXCN UJXBV CBQZB VVSZJ SWSWC JCBGB XDCUW NQTQJ CZKBN FUJDQ JCGZV MWSWQ VVAMJ JKBBX JDSYV QLUGB KNSZB EGCUS WQUUD QFSUY SQNSU

$ python
>>> message = "CGZNL YJBEN QYDLQ ZQSUQ NZCYD SNQVU BFGBK GQUQZ QSUQN UZCYD SNJDS UDCXJ ZCYDS NZQSU QNUZB WSBNZ QSUQN UDCXJ CUBGS BXJDS UCTYV SUJQG WTBUJ KCWSV LFGBK GSGZN LYJCB GJSZD GCHMS UCJCU QJLYS BXUMA UJCJM JCBGZ CYDSN CGKDC ZDSQZ DVSJJ SNCGJ DSYVQ CGJSO JCUNS YVQZS WALQV SJJSN UBTSX COSWG MTASN BXYBU CJCBG UWBKG JDSQV YDQAS JXBNS OQTYV SKCJD QUDCX JBXQK BMVWA SNSYV QZSWA LWAKB MVWAS ZBTSS QGWUB BGJDS TSJDB WCUGQ TSWQX JSNRM VCMUZ QSUQN KDBMU SWCJJ BZBTT MGCZQ JSKCJ DDCUE SGSNQ VUJDS SGZNL YJCBG UJSYY SNXBN TSWAL QZQSU QNZCY DSNCU BXJSG CGZBN YBNQJ SWQUY QNJBX TBNSZ BTYVS OUZDS TSUUM ZDQUJ DSICE SGNSZ CYDSN QGWUJ CVVDQ UTBWS NGQYY VCZQJ CBGCG JDSNB JULUJ STQUK CJDQV VUCGE VSQVY DQASJ UMAUJ CJMJC BGZCY DSNUJ DSZQS UQNZC YDSNC USQUC VLANB FSGQG WCGYN QZJCZ SBXXS NUSUU SGJCQ VVLGB ZBTTM GCZQJ CBGUS ZMNCJ LUDQF SUYSQ NSYNB WMZSW TBUJB XDCUF GBKGK BNFAS JKSSG QGWDC USQNV LYVQL UKSNS TQCGV LZBTS WCSUQ GWDCU JBNCS UESGN SUDSN QCUSW JBJDS YSQFB XUBYD CUJCZ QJCBG QGWQN JCUJN LALJD SSGWB XJDSU COJSS GJDZS GJMNL GSOJD SKNBJ STQCG VLJNQ ESWCS UMGJC VQABM JCGZV MWCGE DQTVS JFCGE VSQNQ GWTQZ ASJDZ BGUCW SNSWU BTSBX JDSXC GSUJS OQTYV SUCGJ DSSGE VCUDV QGEMQ ESCGD CUVQU JYDQU SDSKN BJSJN QECZB TSWCS UQVUB FGBKG QUNBT QGZSU QGWZB VVQAB NQJSW KCJDB JDSNY VQLKN CEDJU TQGLB XDCUY VQLUK SNSYM AVCUD SWCGS WCJCB GUBXI QNLCG EHMQV CJLQG WQZZM NQZLW MNCGE DCUVC XSJCT SQGWC GJKBB XDCUX BNTSN JDSQJ NCZQV ZBVVS QEMSU YMAVC UDSWJ DSXCN UJXBV CBQZB VVSZJ SWSWC JCBGB XDCUW NQTQJ CZKBN FUJDQ JCGZV MWSWQ VVAMJ JKBBX JDSYV QLUGB KNSZB EGCUS WQUUD QFSUY SQNSU"

>>> message.count('A')
20

>>> { k : message.count(k) for k in message }
{'S': 155, 'K': 25, 'E': 17, 'B': 87, 'I': 2, 'V': 56, 'C': 107, 'M': 29, 'Y': 42, 'L': 27, 'W': 47, 'F': 11, ' ': 256, 'A': 20, 'Z': 57, 'H': 2, 'O': 7, 'U': 100, 'X': 29, 'R': 1, 'N': 74, 'Q': 106, 'J': 102, 'G': 81, 'D': 69, 'T': 32}

>>> sorted( [ 3, 2 ] )
[2, 3]

>>> { k : message.count(k) for k in message }.items()
dict_items([('S', 155), ('K', 25), ('E', 17), ('B', 87), ('I', 2), ('V', 56), ('C', 107), ('M', 29), ('Y', 42), ('L', 27), ('W', 47), ('F', 11), (' ', 256), ('A', 20), ('Z', 57), ('H', 2), ('O', 7), ('U', 100), ('X', 29), ('R', 1), ('N', 74), ('Q', 106), ('J', 102), ('G', 81), ('D', 69), ('T', 32)])

>>> [ (value, key) for (key, value) in { k : message.count(k) for k in message }.items()]
[(155, 'S'), (25, 'K'), (17, 'E'), (87, 'B'), (2, 'I'), (56, 'V'), (107, 'C'), (29, 'M'), (42, 'Y'), (27, 'L'), (47, 'W'), (11, 'F'), (256, ' '), (20, 'A'), (57, 'Z'), (2, 'H'), (7, 'O'), (100, 'U'), (29, 'X'), (1, 'R'), (74, 'N'), (106, 'Q'), (102, 'J'), (81, 'G'), (69, 'D'), (32, 'T')]

>>> sorted([ (value, key) for (key, value) in { k : message.count(k) for k in message }.items()])
[(1, 'R'), (2, 'H'), (2, 'I'), (7, 'O'), (11, 'F'), (17, 'E'), (20, 'A'), (25, 'K'), (27, 'L'), (29, 'M'), (29, 'X'), (32, 'T'), (42, 'Y'), (47, 'W'), (56, 'V'), (57, 'Z'), (69, 'D'), (74, 'N'), (81, 'G'), (87, 'B'), (100, 'U'), (102, 'J'), (106, 'Q'), (107, 'C'), (155, 'S'), (256, ' ')]


```


