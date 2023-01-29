# Oracle常用函数分类总结

> 一直使用Oracle的各种函数，但是一直没有整理归类。

## 一、字符函数

| 函数                     | 说明                                                                 |
| ------------------------ | -------------------------------------------------------------------- |
| ASCII(X)                 | 返回字符X的ASCII码                                                   |
| CONCAT(X,Y)              | 连接字符串X和Y                                                       |
| INSTR(X,STR[,START][,N]) | 从X中查找str，可以指定从start开始，也可以指定从n开始                 |
| LENGTH(X)                | 返回X的长度                                                          |
| LOWER(X)                 | X转换成小写                                                          |
| UPPER(X)                 | X转换成大写                                                          |
| TRIM([TRIM_STR  FROM]X)  | 把X的两边截去trim_str字符串，缺省截去空格                            |
| LTRIM(X[,TRIM_STR])      | 把X的左边截去trim_str字符串，缺省截去空格                            |
| RTRIM(X[,TRIM_STR])      | 把X的右边截去trim_str字符串，缺省截去空格                            |
| REPLACE(X,old,new)       | 在X中查找old，并替换成new                                            |
| SUBSTR(X,start[,length]) | 返回X的字串，从start处开始，截取length个字符，缺省length，默认到结尾 |
|concat(str1, str2)|l两个字符串拼接，多个可用 \|\| 拼接 或者 concat函数嵌套|

## 二、数字函数

|函数|说明|示例|
|-------|-------|-------|
|ABS(X)|X的绝对值|ABS(-3)=3|
|ACOS(X)|X的反余弦|ACOS(1)=0|
|COS(X)|余弦|COS(1)=0.54030230586814|
|CEIL(X)|大于或等于X的最小值|CEIL(5.4)=6|
|FLOOR(X)|小于或等于X的最大值|FLOOR(5.8)=5|
|LOG(X,Y)|X为底Y的对数|LOG(2，4)=2|
|MOD(X,Y)|X除以Y的余数|MOD(8，3)=2|
|POWER(X,Y)|X的Y次幂|POWER(2，3)=8|
|ROUND(X[,Y])|X在第Y位四舍五入|ROUND(3.456，2)=3.46; ROUND(351.654,-2)=400|
|SQRT(X)|X的平方根|SQRT(4)=2|
|TRUNC(X[,Y])|X在第Y位截断|TRUNC(3.456，2)=3.45; TRUNC (351.654,-2)=300|

## 三、日期函数

| 函数 | 说明 |
| --------------- | ------------------------------------------------------------- |
| ADD_MONTHS(d,n) | 在某一个日期d上，加上指定的月数n，返回计算后的新日期 |
| LAST_DAY(d)     | 返回指定日期当月的最后一天 |
| ROUND(d[,fmt])  | 返回一个以 fmt 为格式的四舍五入日期值， d 是日期， fmt 是格式 |
| EXTRACT(fmt FROM d) |  提取日期中的特定部分|

## 四、转换函数

| 函数                  | 说明                                                  |
| --------------------- | ----------------------------------------------------- |
| TO_CHAR(d \| n[,fmt]) | 把日期和数字转换为制定格式的字符串。Fmt是格式化字符串 |
| TO_DATE(X,[,fmt])     | 把一个字符串以fmt格式转换成一个日期类型               |
|     TO_NUMBER(X,[,fmt])                  |                              把一个字符串以fmt格式转换为一个数字                         |

## 五、聚合函数

| 函数  | 说明     |
| ----- | -------- |
| AVG   | 平均值   |
| SUM   | 求和     |
| MIN   | 最小值   |
| MAX   | 最大值   |
| COUNT | 数据统计 |

## 六、分析函数

分析函数：用于计算基于组的某种聚合值，它和聚合函数的不同之处是对于每个组返回多行，而聚合函数对于每个组只返回一行。

Oracle分析函数的语法结构：
```
select Analysis_function()OVER([partition by 字段][order by 字段 [windos]]) as 统计值 from table
```

语法解析：
    1、Analysis_function：指定分析函数名，常用的分析函数有sum、max、first_value、last_value、rank、row_number等等。
    2、over()：开窗函数名，
-     partition by指定进行数据分组的字段
-     order by指定进行排序的字段
-     windos指定数据窗口（即指定分析函数要操作的行数），使用的语法形式大概如下：
  
    over(partition by xxx order by yyy rows between zzz)
    
## 七、其他函数

| 函数                                                       | 说明                                                                                         |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| NVL(x,value)                                               | 如果X为空，返回value，否则返回X                                                              |
| NVL2(x,value1,value2)                                      | 如果x非空，返回value1，否则返回value2                                                        |
| decode(条件,值1,返回值1,值2,返回值2,...值n,返回值n,缺省值) | 当字段或字段的运算的值等于值1时，该函数返回值2，否则返回值3。当然值1，值2，值3也可以是表达式 |
|LISTAGG(expr, str) within group(order by clause)|实现对列值的拼接|
