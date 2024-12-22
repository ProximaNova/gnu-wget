# gnu-wget

This edit to Wget does this: .

As of https://github.com/ProximaNova/gnu-wget/tree/1896e483c693c6ba4713b96358cbf81df03a3465
```
$ TZ=UTC ./wget-edit/wget-1.24.5/src/wget -nc https://example.com/
--2024-12-22 22:35:33--  https://example.com/[...]‘index.html’ saved [1256/1256][\n]
$ echo $?
0
$ TZ=UTC ./wget-edit/wget-1.24.5/src/wget -nc https://example.com/
File ‘index.html’ already there; not retrieving.[\n]
$ echo $?
1
$ TZ=UTC ./wget-edit/wget-1.24.5/src/wget -nc https://example.com/ -O index.html
File ‘index.html’ already there; not retrieving.
$ echo $?
1
$ # consistent
```

GNU Wget before the edit:
```
$ TZ=UTC wget -nc https://example.com/
--2024-12-22 22:42:02--  https://example.com/[...]‘index.html’ saved [1256/1256][\n]
$ echo $?
0
$ TZ=UTC wget -nc https://example.com/
File ‘index.html’ already there; not retrieving.[\n]
$ echo $?
0
$ TZ=UTC wget -nc https://example.com/ -O index.html
File ‘index.html’ already there; not retrieving.
$ echo $?
1
$ # inconsistent
```
