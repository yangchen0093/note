### 【2018-05-29】
# SSM
## @#￥1.ajax请求后台报错404
#### *我的原因：
搭建ssm框架的配置文件都是从已有项目中复制过来的，web.xml中springMVC dispatcher的url-pattern是'*.do'，而controller的类方法的resultmapping以'.action'结尾，因此报错404。
#### *其他原因：
没有配置@RequestMapping

<br>

### 【2018-05-30】
# Mybatis
## @#￥1.pagehelper分页sql的执行异常
mapper中的sql(sql1)：  
```
SELECT <include refid="Base_Column_List"/> FROM users WHERE status=0
```
控制台打印显示在执行(sql1)之前又执行了一条sql(sql2)：  
```
SELECT count(*) FROM users WHERE status=0
```
mapper中的sql(sql3)：
```
SELECT <include refid="Base_Column_List"/> FROM users WHERE #{type} LIKE #{input} AND status = 0
```
控制台打印显示只执行的sql(sql4)：
```
SELECT count(*) FROM users WHERE #{type} LIKE #{input} AND status = 0
```
#### *我的原因：
分页使用了mybatis插件pagehelper，控制台中执行的(sql2)应是pagehelper为了计算页码执行的sql语句，也就是说(sql1)和(sql2)都会执行。  
至于为什么只执行了(sql3)而没有执行(sql4)是因为(sql4)存在语法错误，应该写成:
```
SELECT count(*) FROM users WHERE account LIKE #{input} AND status = 0
```

<br>

## @#￥2.mybatis if中判断参数是否等于某个具体值
错误写法，报错说 list_resigned_staff 找不到：
```
<if test="type == list_resigned_staff">
```
正确写法：

`<if test='type == "list_resigned_staff"'>`


<br>

# IDEA
## @#￥1.jdk版本的设置
#### *问题描述：
jdk7以后switch支持使用String，IDEA中项目使用的jdk为1.7，但是switch使用string仍然报错
#### *解决方法：
`打到Project Structure -> Project -> Project Language Level -> 改成7`

<br>