## Database连接类的简单封装

### 配置文件
在项目的resources目录下新建一个名为dbconfig的Resource Bundle。并在里面输入数据库的基本信息和驱动名.  
e.g.  

    url =jdbc:mysql://127.0.0.1/test?useSSL=false
    driver=com.mysql.jdbc.Driver
	username=root
	password=root 

### 如何使用
导入SqlHelper.jar包后，import DB.SqlHelper; 用SqlHelper静态调用各个函数。

### API

    /**
    * return sql.connection
    */
    SqlHelper.getConnection()
  
  
	/**
    * return ResultSet
    * the result of simple Query 
    */
    SqlHelper.executeQuery(String sql,String parameters[])
    
    /**
    * void
    * Update simple update sql
    */
    SqlHelper.executeUpdate(String sql,String [] parameters)
    
    /**
    * void
    * Update many sql at the same time
    * consider transation
    */
    SqlHelper.executeUpdateMore(String sql[],String [] parameters)
    
    /**
    * void
    */
    SqlHelper.callPro1(String sql,String [] parameters)
    
    
	/**
    * void
    * release resource
    */
    SqlHelper.close(ResultSet rs,Statement ps,Connection ct)
    
### 实例
    
    String sql = "select * from person";//SQL语句

    Connection ct = SqlHelper.getConnection();
    String parameters[]={};
    ResultSet rs=SqlHelper.executeQuery(sql, parameters);    
