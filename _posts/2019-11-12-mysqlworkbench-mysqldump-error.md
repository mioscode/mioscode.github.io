---
title: "(MySQL Workbench) MySQL Dump ERROR"
categories:
  - MySQL Workbench
tags:
  - MySQL
  - mysqldump
comments: true
---

# MySQL Workbench - MySQL Dump ERROR
## 내용
MySQL Workbench에서 Data Export 시,
Unknown table 'column_statistics' in information_schema (1109) Error 나오면서 실패

```
$ mysql -V
mysql  Ver 15.1 Distrib 10.3.13-MariaDB, for osx10.14 (x86_64) using readline 5.1
```
 
## 해결
MySQL Workbench -> Preference -> Administration -> Path to mysqldump Tool: /usr/local/Cellar/mariadb/10.3.13_1/bin/mysqldump