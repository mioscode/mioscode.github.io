---
title: Jekyll - (mac) mysql - Can't read dir of '/usr/local/etc/my.cnf.d' 해결
categories:
  -  mysql
tags:
  - mac
  - mysql
  - error
comments: true
---

## Error 
```
$ mysql.server start

/usr/local/Cellar/mariadb/10.3.13_1/bin/my_print_defaults: Can't read dir of '/usr/local/etc/my.cnf.d' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted
Starting MariaDB
./usr/local/Cellar/mariadb/10.3.13_1/bin/my_print_defaults: Can't read dir of '/usr/local/etc/my.cnf.d' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted
/usr/local/Cellar/mariadb/10.3.13_1/bin/my_print_defaults: Can't read dir of '/usr/local/etc/my.cnf.d' (Errcode: 2 "No such file or directory")
Fatal error in defaults handling. Program aborted
190604 10:28:40 mysqld_safe Logging to '/usr/local/var/mysql/macbook-2.local.err'.
190604 10:28:40 mysqld_safe Starting mysqld daemon with databases from /usr/local/var/mysql
/usr/local/bin/mysql.server: line 264: kill: (5900) - No such process
 ERROR!
```

## Solution
```
✗ mkdir /usr/local/etc/my.cnf.d

✗ mysql.server start

Starting MariaDB
.190604 10:29:02 mysqld_safe Logging to '/usr/local/var/mysql/macbook-2.local.err'.
190604 10:29:02 mysqld_safe Starting mysqld daemon with databases from /usr/local/var/mysql
 SUCCESS!
```



# Reference
[https://github.com/Homebrew/legacy-homebrew/issues/31760](https://github.com/Homebrew/legacy-homebrew/issues/31760)
