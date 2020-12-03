# Yasp
(Description is not finished)

Yasp - Search typos in stdout, files, directories, and websites by using Yandex.Speller API

Author: Andrey Klychkov <aaklychkov@mail.ru>

Licence: GNU GPL v3

Version: 0.8.0

Date: 30-10-2020

### Description:

For more information about Yandex.Speller, refer to  <https://tech.yandex.ru/speller>.

Search typos in a text file "-f", text files in a directory "-d" (with "-r" recursively) and websites "-u".

Checking files in html format has not available yet (maybe later).

### Requirements:
Python 3+, bs4, Internet connection

### Synopsis:
```
yasp [-h] [-r] [-s] [-f FILE | -d DIR | -u URL | --version]
```

### Options:
```
  -h, --help            show this help message and exit
  -f FILE, --file FILE  path to a FILE
  -d DIR, --dir DIR     path to a DIR
  -r, --recursive       search recursively
  -s, --stat            print statistics
  -u URL, --url URL     path to a web page (NOT AVAILABLE YET)
  --version             show version and exit
```

### Examples:

Passing text via stdin:
```
echo "Helllo" | yast
stdin : line [0] : helllo > hello, helloo, heello
```

Passing a file name:
```
yasp -f test.txt
testdir/test.txt : line [1] : programer > programmer, programmers, program
testdir/test.txt : line [1, 2] : requirenments > requirements, requiredments, requirement
testdir/test.txt : line [29, 147] : datbase > database, databases, datebase
testdir/test.txt : line [108, 125] : complited > completed, complete, compiled
testdir/test.txt : line [202] : computes > computers, computer, compute
testdir/test.txt : line [254] : nitification > nitrification, notification, notifications
testdir/test.txt : line [369] : inforamtion > information, informations, infromation
```

Print statistics:
```
yasp -f test.txt -s
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

Parse all files in a directory recursively, show statistics:
```
yasp -d testdir -r -s
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
