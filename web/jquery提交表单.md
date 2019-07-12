### 标题

无法通过jquery提交表单

------

### 时间

2019-3-25

------

### 错误提示

点了按钮不通过js提交而是直接提交

---

### 原因

type必须要设置为button,不然默认为submit,会自动提交而不会经过js 

------

### 解决方法

```xml
<script type="text/javascript" src="js/jquery-3.3.1.min.js"></script>
<script type="text/javascript">
	$(function(){    //要加这行才会初始化
		$('#sub').click(function(){
			$.post("login",$('#forms').serialize(),function(result){    //.serialize()和.serializeArray()可以把表单等序列化为json
				if (result.success==true)
					console.log("walcome "+result.name);
				else 
					console.log("error");
			},"json")
		});
	})
</script>


<form id="forms">
	name:<input type="text" name="name"/><br>
	password:<input type="password" name="password"/><br> 	
	<button type="button" id="sub">submit</button>     //这里的type必须要设置为button,不然默认为submit,会自动提交而不会经过js 
</form>
```

---

### 注释



------

### 获取路径

https://www.cnblogs.com/klwyrn/p/5955152.html

------



