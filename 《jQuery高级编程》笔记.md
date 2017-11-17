# 《jQuery高级编程》笔记 #

# 第一章jQuery入门 #
## 1.1jQuery引用 ##

	<scripttype="text/javascript"src="jquery.min.js"></script>

## 1.2示例 ##

	jQuery(document).ready(function(){
		alert('HelloWorld!');
	});

## 1.3类型检查 ##

	对象					类型检查表达式
	String				typeofobject==="string"
	Number				typeofobject==="number"
	Boolean				typeofobject==="boolean"
	Object				typeofobject==="object"
	Element				object.nodeType
	null				object===null
	null				object==null

类型检查的 `jQuery` 方法

	对象					类型检查表达式
	PlainObject			jQuery.isPlainObject(object)
	Function			jQuery.isFunction(object)
	Array				jQuery.isArray(object)

对 `undefined` 进行类型检查的方法

	对象					类型检查表达式
	GlobalVariables		typeofvariable==="undefined"
	LocalVariables		variable===undefined
	Properties			object.prop===undefined

# 第二章JavaScript基础 #

## 2.1理解数值 ##

	varnum=1234.5678;
	num.toFixed(2);				//按照固定位数的小数格式化数值(小数点后有效位数)，四舍五入
	num.toPrecision(8);			//按照固定位数的小数格式化数值(数值有效位数)，四舍五入
	Infinity					//无穷大
	NaN							//"非数值"NotaNumber
	Math.round(num)				//取整数，四舍五入

## 2.2字符串 ##

	varstring="TestString";
	string.indexOf("S");		//5,获取字符在字符串中第一次出现的位置
	string.charAt(5);			//"S",获取字符串中下标为5的字符

## 2.3布尔类型 ##

	'',NaN,null,undefined,0,false为判断值时均为false，其他的任何值都是true.
	typeofNaN//number
	1=="1"//true
	1==="1"//false

## 2.4JavaScript各种数据类型 ##

	Number
	String
	Boolean
	Object
	Function
	Array
	Date
	RegEx
	Null
	Undefined
	Error
		EvalError
		RangeError
		ReferenceError
		SyntaxError
		TypeError
		URIError

## 2.5理解对象 ##
	varmyObject=newObject();
	
	functionZombie(name){
		this.name=name;
	}
	varsmallZombie=newZombie("Booger");
	
	vartestObject1={};
	vartestObject2={
		"property1":"astringvalue",
		"property2":testObject1,
		"method1":function(){
			console.log("testObject2method1");
		}
	};
	testObject2['property1']//astringvalue
	testObject2.property1//astringvalue
	
	varobj={
		'property1':1,
		'property2':2
	};
	vari;
	for(iinobj){
		console.log(i);
	}
	//property1
	//property2
	
	funtionMonster(type){
		this.type=type;
	}
	Monster.prototype.getType=function(){
		returnthis.type;
	}
	functionZombie(name){
		this.name=name;
	}
	Zombie.prototype=newMonster();
	Zombie.prototype.eatPeople=function(){
		console.log('Testeslikechicken');
	}

## 2.6作用域和闭包 ##

## 2.7理解访问级别 ##

## 2.8使用模块 ##

## 2.9JavaScript数组 ##

## 2.10扩展类型 ##

	String.prototype.boolean=function(){
		return"true"==this;
	};
	'true'.boolean();//true
	'false'.boolean();//false
	
	Function.prototype.method=function(name,func){
		this.prototype[name]=function;
	};
	String.method('boolean',function(){
		return'true'==this;
	});
	'true'.boolean();//True

## 2.11JavaScript最佳实践 ##

- (1)数组转型

		parseInt("010",10);//Good
		+"010";//Better

- (2)比较两个值时最好使用(===)
- (3)定义对象时，最后一个属性或方法后面不要使用逗号。
- (4)限制使用eval()函数。
- (5)使用分号作为语句的结尾
- (6)避免使用全局变量，总是使用var来声明变量。
- (7)对函数名使用首字母大写的表示该函数作为new操作符的构造函数，但不要对其他任何函数的函数名使用首字母大写。
- (8)不要使用with语句。
- (9)在循环中创建函数应该谨慎小心。

# 第三章jQuery核心技术 #
## .1jQuery脚本的结构 ##

	方法			分类		描述
	.ready()		事件		声明函数，当DOM完全加载后运行
	.click()		事件		为匹配的元素集设置click事件处理程序
	.ajax()			Ajax		jQuery的Ajax工具函数
	.addClass()		CSS			为匹配的元素集添加一个CSS类
	.removeClass()	CSS			为匹配的元素集移除一个CSS类
	.attr()			Attributes	获取或设置指定属性的值
	.html()			Attributes	获取或设置匹配的第一个元素的HTML内容
					/DOM插入	
	.type()			工具方法	判断一个对象在JavaScript内部的类型

### 3.1.1工具函数 ###
	1.对象
		$.type(object);//检查对象的类型
		$.isEmptyObject(object);//检查对象是否包含任何属性
		$.isPlainObject(object);//检查对象是不是一个含有任何属性，但是对象必须是一个Object的实例。
		$.extend(obj1,obj2);//将一个或多个对象的属性合并的一个目标对象之中。
	2.函数
		$.isFunction(function(){
			console.log('dosomething');
		});//检查对象是否是一个函数。
		$.noop();//空函数
	3.数组操作
		$.isArray();//判断对象是否是一个数组
		$.makeArray();//将一个类似于数组的对象转换成一个数组
		$.merge();//合并数组
		$.unique();//从DOM元素数组中移除重复的元素
		$.each();//遍历数组
		$.map();//遍历对象或数组
	4.数据结构
		$.queue();//队列
		$.clearQueue();//移除队列所有未被执行的函数
		$.dequeue();//执行并移除队列中的一个函数
	5.字符串
		$.trim(string);//移除字符串首尾的空格
	6.其他工具方法
		$.contains();//检查一个DOM节点是否是另一个节点的子节点
		$.isWindow();//区分iframe和浏览器窗口
		$.now();//用于获取当前时间
		$.support();//检查浏览器特性
		$.globalEval();//执行代码，变量为全局变量
		$.isXMLDoc();//检查一个DOM节点是否属于一个XML文档
		$.parseJSON();//将JSON串转成一个对象

## 3.2非侵入式JavaScript ##

