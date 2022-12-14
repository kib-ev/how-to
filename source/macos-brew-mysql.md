# How to install `mySQL` on `MacOs` with `Homebrew`

```
brew install mysql
```

After install check `mysql` version and remember the path

```
$ brew info mysql
-----------------------------------------------------------------
mysql: stable 8.0.30 (bottled)
...
/usr/local/Cellar/mysql/8.0.30 (312 files, 297MB) *
...
```

To start server

```
$ brew services start mysql
-----------------------------------------------------------------
==> Successfully started `mysql` (label: homebrew.mxcl.mysql)
```

Create new alias for `mysql` if needed

```
$ nano ~/.bash_profile
```

Add new row

```
alias mysql=/usr/local/Cellar/mysql/8.0.30/bin/mysql
```

To save and exit from nano press `Ctrl+X` `Y` `Enter`

```
$ source ~/.bash_profile
```

Now we can type 

```
$ mysql -v
-----------------------------------------------------------------
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

I get error message. To solve do the following

```
$ brew services stop mysql
$ sudo pkill mysqld
$ brew postinstall mysql
$ brew services start mysql
$ mysql -uroot
-----------------------------------------------------------------
mysql>
```

Set new password for `root`

```
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'secret';
-----------------------------------------------------------------
Query OK, 0 rows affected (0.12 sec)
```

After setting the password to open `mysql` cli, need to type

```
$ mysql -u root -p
-----------------------------------------------------------------
Enter password: 
Welcome to the MySQL monitor.  ...
```

To exit `mysql` cli just type

```
mysql> exit;
-----------------------------------------------------------------
Bye
```