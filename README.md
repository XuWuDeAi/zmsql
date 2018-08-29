# zmsql
## About
一个sql防注入框架,里面自带sql构造器，可用在后端和安卓
#### [Download](https://raw.githubusercontent.com/XuWuDeAi/zmsql/master/zmsql.jar)<br>

## 用法：

#### sql防注入
```groovy
	String attribute ="test";
	String count="1";
	String sql = "SELECT *  FROM `article` AS a WHERE a.`attribute`='%s'  ORDER BY a.`createtime` LIMIT 0,%s";
	try {
		sql = ZmSql.format(sql, attribute, count);
		//sql = ZmSql.format(sql, attribute, count,...,...);
		//also you can add more
	} catch (Exception e) {
		e.printStackTrace();
	}
	System.out.println(sql);
```
#### sql构造器
```groovy
	SqlUpdate update = new SqlUpdate("student");
	update.add2("sex", true);
	update.add2("phone", "1234567");
	System.out.println(update);

	SqlWhere where = new SqlWhere();
	where.add2("id", 20180002);
	System.out.println(where);

	SqlInsert insert = new SqlInsert("gg");
	insert.add2("phone", "1234567");
	System.out.println(insert);
```
