# MySQL
### 【2018-04-xx】
## @#￥1.想要查询某条记录在数据库表中的实际行数（比如某条记录的id是12但是这条记录其实是表中的第一条数据）
```
Select id,(@rownum:=@rownum+1) as rowNo
From table_name,
(Select (@rownum :=0) ) b;
```

<br><br>

### 【2018-05-30】
## @#￥2.and和or连用
错误写法：
```
status = 0 and username like '%g%' or account like '%g%'
```
正确写法，将or的条件用括号括起来：
```
status = 0 and (username like '%g%' or account like '%g%')
```