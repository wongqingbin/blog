---
title: mysql指定日期的数据统计
tags: countdate
categories: sql
date: 2020-06-18 22:40:24
---
SQL查询之指定日期内的数据。  
例如：今天、本周、本月、本季度、今年、近半年、近一个月、近7天
<!-- more -->

## mysql有关日期条件的查询语句

```sql
# 查询今天 当天
SELECT * FROM `table_name` WHERE TO_DAYS(col_name)=TO_DAYS(NEW());  # CURDATE()或NEW()

# 获取本周
SELECT * FROM `table_name` WHERE YEARWEEK(DATE_FORMAT(col_name,'%Y-%m-%d'))=YEARWEEK(NEW());

# 获取本月
SELECT * FROM `table_name` WHERE DATE_FORMAT(col_name,'%Y-%m')=DATE_FORMAT(NEW(),'%Y-%m');

# 获取本季度
SELECT * FROM `table_name` WHERE QUARTER(col_name)=QUARTER(NEW());

# 获取本年
SELECT * FROM `table_name` WHERE YEAR(col_name)=YEAR(NEW());

################################################################################
# 获取某年某月的数据, 第二种方式更常用DATE_FORMAT
SELECT * FROM `table_name` WHERE YEAR(col_name)=2020 AND MONTH(col_name)=6;
SELECT * FROM `table_name` WHERE DATE_FORMAT(col_name,'%Y-%m')='2020-06';  # %Y-%m对应2020-06  %Y-%c对应2020-6  区别0
################################################################################

# 获取近1月
SELECT * FROM `table_name` WHERE DATE_SUB(NEW(), INTERVAL 1 MONTH) <= DATE(col_name);
# 获取近1星期 或 近7天数据
SELECT * FROM `table_name` WHERE DATE_SUB(NEW(), INTERVAL 7 DAY) <= DATE(col_name);
# 获取近1年
SELECT * FROM `table_name` WHERE YEAR(col_name)=YEAR(DATE_SUB(NEW(),INTERVAL 1 YEAR));
# 获取近1季度
SELECT * FROM `table_name` WHERE QUARTER(col_name)=QUARTER(DATE_SUB(NEW(),INTERVAL 1 QUARTER));

#########################################

# 获取近半年内每个月的统计
SELECT
 COUNT(*) as nums, DATE_FORMAT( col_name, '%Y-%m' ) as date_time
FROM
 `table_name`
WHERE
 DATE_SUB( NEW(), INTERVAL 6 MONTH ) <= DATE( col_name )
GROUP BY
 date_time;
# 打印结果 ################
# nums  |  data_time
#  10   |    2020-01
#  50   |    2020-02
#  90   |    2020-03
#  30   |    2020-04
##########################

########################################################
# 数据库日期类型使用 datetime 即可
########################################################
```

<br/><br/>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
