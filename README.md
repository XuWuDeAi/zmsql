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
	//运行结果:SELECT *  FROM `article` AS a WHERE a.`attribute`='test'  ORDER BY a.`createtime` LIMIT 0,1
	//说明：ZmSql.format会对你的参数进行特定的防注入转义，转义完后会将参数依次替换sql里的%s
	
```
#### sql构造器
```groovy
	SqlUpdate update = new SqlUpdate("student");
	update.add2("sex", true);
	update.add2("phone", "1234567");
	System.out.println(update);
        //运行结果: UPDATE `student` SET `sex`='1',`phone`='1234567' 

	SqlWhere where = new SqlWhere();
	where.add2("id", 20180002);
	System.out.println(where);
	//运行结果: WHERE (`id`='20180002')

	SqlInsert insert = new SqlInsert("gg");
	insert.add2("phone", "1234567");
	System.out.println(insert);
	//运行结果: INSERT INTO `gg`(`phone`) VALUES ('1234567')
	
```
