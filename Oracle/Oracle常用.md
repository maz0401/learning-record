# Oracle基本使用

## Oracle日期相关

1. 获取日期后，加减月份操作

```
# -n 标识减去n个月，n标识增加几个月
SELECT ADD_MONTHS(sysdate, -12) AS "当前时间减一年" FROM dual;
```

2. 日期和字符转换函数用法（to_date,to_char）

```
select to_char(sysdate,'yyyy-mm-dd hh24:mi:ss') as nowTime from dual;   //日期转化为字符串  
select to_char(sysdate,'yyyy')  as nowYear   from dual;   //获取时间的年  
select to_char(sysdate,'mm')    as nowMonth  from dual;   //获取时间的月  
select to_char(sysdate,'dd')    as nowDay    from dual;   //获取时间的日  
select to_char(sysdate,'hh24')  as nowHour   from dual;   //获取时间的时  
select to_char(sysdate,'mi')    as nowMinute from dual;   //获取时间的分  
select to_char(sysdate,'ss')    as nowSecond from dual;   //获取时间的秒
```

3. 计算时间差

```
注:oracle时间差是以天数为单位,所以换算成年月,日
 select floor(to_number(sysdate-to_date('2007-11-02 15:55:03',
 'yyyy-mm-dd hh24:mi:ss'))/365) as spanYears from dual        //时间差-年
 select ceil(moths_between(sysdate-to_date('2007-11-02 15:55:03',
 'yyyy-mm-dd hh24:mi:ss'))) as spanMonths from dual           //时间差-月
 select floor(to_number(sysdate-to_date('2007-11-02 15:55:03',
 'yyyy-mm-dd hh24:mi:ss'))) as spanDays from dual             //时间差-天
 select floor(to_number(sysdate-to_date('2007-11-02 15:55:03',
 'yyyy-mm-dd hh24:mi:ss'))*24) as spanHours from dual         //时间差-时
 select floor(to_number(sysdate-to_date('2007-11-02 15:55:03',
 'yyyy-mm-dd hh24:mi:ss'))*24*60) as spanMinutes from dual    //时间差-分
 select floor(to_number(sysdate-to_date('2007-11-02 15:55:03',
 'yyyy-mm-dd hh24:mi:ss'))*24*60*60) as spanSeconds from dual //时间差-秒
```
4.查找月的第一天,最后一天
```
SELECT Trunc(Trunc(SYSDATE, 'MONTH') - 1, 'MONTH') First_Day_Last_Month,
    Trunc(SYSDATE, 'MONTH') - 1 / 86400 Last_Day_Last_Month,
    Trunc(SYSDATE, 'MONTH') First_Day_Cur_Month,
    LAST_DAY(Trunc(SYSDATE, 'MONTH')) + 1 - 1 / 86400 Last_Day_Cur_Month
FROM dual;
```

## Oracle TO_DATE格式(以时间:2007-11-02 13:45:25为例)

```
Year:

yy     two digits   两位年                显示值:07
yyy    three digits 三位年                显示值:007
yyyy   four digits  四位年                显示值:2007
Month:

mm     number       两位月               显示值:11
mon    abbreviated  字符集表示           显示值:11月,若是英文版,显示nov
month  spelled out  字符集表示           显示值:11月,若是英文版,显示november
Day:

dd     number         当月第几天         显示值:02
ddd    number         当年第几天         显示值:02
dy     abbreviated    当周第几天简写     显示值:星期五,若是英文版,显示fri
day    spelled out    当周第几天全写     显示值:星期五,若是英文版,显示friday 
Hour:

hh     two digits     12小时进制        显示值:01
hh24   two digits     24小时进制        显示值:13
Minute:

mi    two digits      60进制            显示值:45
Second:

ss    two digits      60进制            显示值:25
其它

Q     digit           季度              显示值:4
WW    digit           当年第几周         显示值:44
W     digit           当月第几周         显示值:1
24小时格式下时间范围为： 0:00:00 - 23:59:59....

12小时格式下时间范围为： 1:00:00 - 12:59:59...
```