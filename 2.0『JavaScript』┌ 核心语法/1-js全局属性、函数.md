

# 全局属性

Infinity        代表正无穷大的数值
NaN             代表某个值不是数字（not a number）
undefined       代表未定义的值


# 全局函数

encodeURI(uri)             编码(, / ? : @ & = + $ # 等具有特殊含义的ASCII符号是不会进行转义)，可用encodeURIComponent()
decodeURI(uri)             解码某个URI，对应 encodeURI() 函数编码
encodeURIComponent(uri)    编码，该方法不会对 ASCII 字母和数字进行编码，以及- _ . ! ~ * ' ( )
decodeURIComponent(uri)    解码某个URI，对应 encodeURIComponent() 函数编码
escape(str)                编码，不会对 ASCII 字母和数字进行编码，以及 * @ - _ + . / 
unescape(str)              解码，对应escape（）
eval(str)                  把字符串作为脚本代码执行，谨慎使用
isFinite(num)              检测参数是否是无穷大      
isNaN(val)                 检测参数是否是非数字
Number(obj)                把对象的值转为数字，如果无法转为数字，返回NaN
String(obj)                把对象的值转为字符串
parseInt(str,radix)        把字符串转为整数，radix代表进制，默认是10
parseFloat(string)         把字符串转为浮点数，无法转换返回NaN









# encodeURI 与 encodeURIComponent 区别

encodeURI ， encodeURIComponent ，escape 三者都是js对字符串进行编码，主要对比一下区别

### 首选，为什么要进行URL编码

我们都知道Http协议中参数的传输是"key=value"这种简直对形式的，如果要传多个参数就需要用“&”符号对键值对进行分割。如"?name1=value1&name2=value2"，这样在服务端在收到这种字符串的时候，会用“&”分割出每一个参数，然后再用“=”来分割出参数值

现在有这样一个问题，如果我的参数值中就包含=或&这种特殊字符的时候该怎么办

比如说“name1=value1”,其中value1的值是“va&lu=e1”字符串，那么实际在传输过程中就会变成这样“name1=va&lu=e1”。我们的本意是就只有一个键值对，但是服务端会解析成两个键值对，这样就产生了奇异。

解决的办法就是对参数进行URL编码

## escape(str)

除了 ASCII 字母、数字和特定的符号外，对传进来的字符串全部进行转义编码，因此如果想对URL编码，最好不要使用此方法。

escape不会编码的字符有69个：*，+，-，.，/，@，_，0-9，a-z，A-Z

使用场景：最好是单纯对非URI的string需要编码的时候使用它

> ECMAScript 3中已经不提倡使用这个函数了，所以我们还是少用吧


## encodeURI(uri)

 encodeURI()对 URI 进行完整的编码，
 
 encodeURI不会进行编码的字符有82个 ：!，#，$，&，'，(，)，*，+，,，-，.，/，:，;，=，?，@，_，~，0-9，a-z，A-Z

 具有特殊含义的 ASCII 标点符号（, / ? : @ & = + $ #）不会进行转义的

 使用encodeURI()编码后的结果是除了空格之外的其他字符都原封不动，只有空格被替换成了%20,encodeURI主要用于直接赋值给地址栏

 ```
 ocation.href=encodeURI("http://www.baidu.com/")

 ```

##  encodeURIComponent()

encodeURIComponent:不会进行编码的字符有71个：!， '，(，)，*，-，.，_，~，0-9，a-z，A-Z

encodeURIComponent编码更很一些，被编码后的字符都变成%xx这样的16进制形式

encodeURIComponent() 方法在编码单个 URIComponent（指请求参 数）应当是最常用的，它可以将参数中的中文、特殊字符进行转义，而不会影响整个URL

```
location.href="http://www.baidu.com?name="+encodeURIComponent("xie")

```

参考：
https://blog.csdn.net/baidu_33033415/article/details/62882479
https://blog.csdn.net/luman1991/article/details/54980722