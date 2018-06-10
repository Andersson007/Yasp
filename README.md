# Yasp
(Description is not finished)

Yasp - Search typos in files and websites by using Yandex.Speller API

Author: Andrey Klychkov <aaklychkov@mail.ru>

Licence: GNU GPL v3

Version: 0.4

Date: 10-06-2018

### Description:

Information about Yandex.Speller is here <https://tech.yandex.ru/speller>.

Search typos in a text file "-f", text files in directory "-d" (with "-r" recursively) and websites "-u".

Check files in html format has not available yet (maybe later).

### Requirements:
Python 3+, bs4, Internet connection

### Synopsis:
```
yasp [-h] [-f FILE | -d DIR | -u URL | --version] [-r]
```

### Options:
```
  -h, --help            show this help message and exit
  -f FILE, --file FILE  path to a FILE
  -d DIR, --dir DIR     path to a DIR
  -r, --recursive       search recursively
  -u URL, --url URL     path to a web page (NOT AVAILABLE YET)
  --version             show version and exit
```

### Examples:

yasp -f test.txt
```
response from Yandex received in 0:00:01.556796

testdir/test.txt : line [1] : programer > programmer, programmers, program
testdir/test.txt : line [1, 2] : requirenments > requirements, requiredments, requirement
testdir/test.txt : line [29, 147] : datbase > database, databases, datebase
testdir/test.txt : line [108, 125] : complited > completed, complete, compiled
testdir/test.txt : line [202] : computes > computers, computer, compute
testdir/test.txt : line [254] : nitification > nitrification, notification, notifications
testdir/test.txt : line [369] : inforamtion > information, informations, infromation

Total statistics:
----------------
lines: 377
words num: 2006
parsed words (alph, >2 symb): 1204
uniq words: 329
chars request: 4010
requests to Yandex: 1
max request len: 4074
execution time: 0:00:01.574109
```

yasp -d testdir -r
```
response from Yandex received in 0:00:04.273587

testdir/test.txt : line [1] : programer > programmer, programmers, program
testdir/test.txt : line [1, 2] : requirenments > requirements, requiredments, requirement
testdir/test.txt : line [29, 147] : datbase > database, databases, datebase
testdir/test.txt : line [108, 125] : complited > completed, complete, compiled
testdir/test.txt : line [202] : computes > computers, computer, compute
testdir/test.txt : line [254] : nitification > nitrification, notification, notifications
testdir/test.txt : line [369] : inforamtion > information, informations, infromation
testdir/subdir/RCHE.txt : line [8, 56] : cloudplatform > cloud platform, cloud platforms, cloudy platform
testdir/subdir/RCHE.txt : line [46, 94] : jaques > jacques, jacque, jacues
testdir/subdir/Vught.txt : line [16] : fied > field, filed, fired
testdir/subdir/Vught.txt : line [31] : readying > reading, readings, relaying
testdir/subdir/Vught.txt : line [36] : cli > clip, click, klip, sli, clin, clit, slip, cell, coli

response from Yandex received in 0:00:00.470344

testdir/subdir/Vught.txt : line [86] : infor > information, in for, inform
testdir/subdir/Vught.txt : line [90] : argu > argue, argument, argued

Total statistics:
----------------
lines: 578
words num: 4319
parsed words (alph, >2 symb): 3007
uniq words: 886
chars request: 11073
requests to Yandex: 2
max request len: 10007
execution time: 0:00:04.778420
```
