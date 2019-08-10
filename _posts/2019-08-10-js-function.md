---
layout: post
title: Functions In JavaScript
tags: JavaScript
categories: Front-End
---

* TOC 
{:toc}

---
# 1.常规函数
javascript常规函数包括以下9个函数:
(1)alert: 显示一个警告对话框,包括一个OK按钮.
(2)confirm:显示一个确认对话框,包括OK,Cancel按钮.
(3)escape: 将字符转换成Unicode码.
(4)eval:计算表达式的结果.
(5)isNaN:测试是(true)否(false)不是一个数字.
(6)parseFloat:将字符串转换成符点数字形式.
(7)parseInt:将符串转换成整数数字形式(可指定几进制).
(8)prompt:显示一个输入对话框,提示等待用户输入.例如:

~~~javascript
<script language="javascript">
<!--
alert("输入错误");
prompt("请输入您的姓名","姓名");
confirm("确定否!");
//-->
</script>
~~~

(9)unescape:解码由escape函数编码的字符.
---

---
# 2.数组函数
javascript数组函数包括以下4个函数:
(1)join:转换并连接数组中的所有元素为一个字符串.例:

```javascript
function JoinDemo() {
    var a,b;
    a=new Array(0,1,2,3,4);
    b=a.join("-");//分隔符
    return(b);//返回的b=="0-1-2-3-4"
}
```

(2)length:返回数组的长度.
例:

~~~javascript
function LengthDemo() {
    var a,l;
    a=new Array(0,1,2,3,4);
    l=a.length;
    return (l);//l==5
}
~~~

(3)reverse:将数组元素顺序颠倒.
例:

~~~javascript
function ReverseDemo() {
    var a,l;
    a=new Array(0,1,2,3,4);
    l=a.reverse();
    return(l);
}
~~~

(4)sort:将数组元素重新排序.
例:

~~~javascript
function SortDemo() {
    var a,l;
    a=new Array("X","y","d","Z","v","m","r");
    l=a.sort();
    return (l);
}
~~~

---


---
# 3.日期函数
javascript日期函数包括以下20个函数:
(1)getDate:返回日期的"日"部分,值为1～31.
例:

~~~javascript
function DateDemo() {
    var d,s="Today'sdateis:";
    d=newDate();
    s+=(d.getMonth()+1)+"/";
    s+=d.getDate()+"/";
    s+=d.getYear();
    return(s);
}
~~~

(2)getDay:返回星期几,值为0～6,其中0表示星期日,1表示星期一,...,6表示星
期六.
例:

~~~javascript
function DateDemo() {
    var d,day,x,s="Todayis:";
    var x=new Array("Sunday","Monday","Tuesday");
    var x=x.concat("Wednesday","Thursday","Friday");
    var x=x.concat("Saturday");
    d=newDate();
    day=d.getDay();
    return(s+=x[day]);
}
~~~

(3)getHouse:返回日期的"小时"部分,值为0～23.
例.

~~~javascript
function TimeDemo() {
    var d,s="The current local time is:";
    var c=":";
    d=newDate();
    s+=d.getHours()+c;
    s+=d.getMinutes()+c;
    s+=d.getSeconds()+c;
    s+=d.getMilliseconds();
    return(s);
}
~~~

(4)getMinutes:返回日期的"分钟"部分,值为0～59.见上例.

(5)getMonth:返回日期的"月"部分,值为0～11.其中0表示1月,2表示3月,...,
11表示12月.见前面的例子.

(6)getSeconds:返回日期的"秒"部分,值为0～59.见前面的例子.

(7)getTime:返回系统时间.

~~~javascript
function GetTimeTest() {
    var d,s,t;
    var MinMilli=1000*60;
    var HrMilli=MinMilli*60;
    var DyMilli=HrMilli*24;
    d=new Date();
    t=d.getTime();
    s="It's been"
    s+=Math.round(t/DyMilli)+"days since 1/1/70";
    return(s);
}
~~~

(8)getTimezoneOffset:返回此地区的时差(当地时间与GMT格林威治标准时间的地区时
差),单位为分钟.

~~~javascript
function TZDemo() {
    var d,tz,s="Thecurrentlocaltimeis";
    d=new Date();
    tz=d.getTimezoneOffset();
    if (tz < 0)
    s+=tz/60+"hoursbeforeGMT";
    else if (tz==0)
    s+="GMT";
    else
    s+=tz/60+"hoursafterGMT";
    return(s);
}
~~~

(9)getYear:返回日期的"年"部分.返回值以1900年为基数,例如1999年为99.前面
有例子.

(10)parse:返回从1970年1月1日零时整算起的毫秒数(当地时间).

~~~javascript
function GetTimeTest(testdate) {
    var d,s,t;
    var MinMilli=1000*60;
    var HrMilli=MinMilli*60;
    var DyMilli=HrMilli*24;
    d=new Date();
    t=Date.parse(testdate);
    s="Thereare"
    s+=Math.round(Math.abs(t/DyMilli))+"days"
    s+="between"+testdate+"and 1/1/70";
    return(s);
}
~~~

(11)setDate:设定日期的"日"部分,值为0～31.

(12)setHours:设定日期的"小时"部分,值为0～23.

(13)setMinutes:设定日期的"分钟"部分,值为0～59.

(14)setMonth:设定日期的"月"部分,值为0～11.其中0表示1月,...,11表示12
月.

(15)setSeconds:设定日期的"秒"部分,值为0～59.

(16)setTime:设定时间.时间数值为1970年1月1日零时整算起的毫秒数.

(17)setYear:设定日期的"年"部分.

(18)toGMTString:转换日期成为字符串,为GMT格林威治标准时间.

(19)setLocaleString:转换日期成为字符串,为当地时间.

(20)UTC函数:返回从1970年1月1日零时整算起的毫秒数,以GMT格林威治标准时间计
算.

---

---
# 4.数学函数
javascript数学函数其实就是Math对象,它包括属性和函数(或称方法)两部分.其中,属性
主要有下列内容:
Math.e:e(自然对数),Math.LN2(2的自然对数),Math.LN10(10的自然对数),Math.LOG2E(e
的对数,底数为2),Math.LOG10E(e的对数,底数为10),Math.PI(π),Math.SQRT1_2(1/2
的平方根值),Math.SQRT2(2的平方根值).
函数有以下18个:
(1)abs:即Math.abs(以下同),返回一个数字的绝对值.

(2)acos:返回一个数字的反余弦值,结果为0～π弧度(radians).

(3)asin:返回一个数字的反正弦值,结果为-π/2～π/2弧度.

(4)atan:返回一个数字的反正切值,结果为-π/2～π/2弧度.

(5)atan2:返回一个坐标的极坐标角度值.

(6)ceil:返回一个数字的最小整数值(大于或等于).

(7)cos:返回一个数字的余弦值,结果为-1～1.

(8)exp:返回e(自然对数)的乘方值.

(9)floor:返回一个数字的最大整数值(小于或等于).

(10)log:自然对数,返回一个数字的自然对数(e)值.

(11)max:返回两个数的最大值.

(12)min:返回两个数的最小值.

(13)pow:返回一个数字的乘方值.

(14)random:返回一个0～1的随机数值.

(15)round:返回一个数字的四舍五入值,类型是整数.

(16)sin:返回一个数字的正弦值,结果为-1～1.

(17)sqrt:返回一个数字的平方根值.

(18)tan:返回一个数字的正切值.

---


---
# 5.字符串函数
javascript字符串函数完成对字符串的字体大小,颜色,长度和查找等操作,共包括以下20
个函数:
(1)anchor:产生一个链接点(anchor)以作超级链接用.anchor设定的链接点的名称,
另一个函数link设定的URL地址.

(2)big:将字体加到一号,与...标签结果相同.

(3)blink:使字符串闪烁,与...标签结果相同.

(4)bold:使字体加粗,与...标签结果相同


(5)charAt:返回字符串中指定的某个字符.

(6)fixed:将字体设定为固定宽度字体,与...标签结果相同.

(7)fontcolor:设定字体颜色,与标签结果相同.

(8)fontsize:设定字体大小,与标签结果相同.

(9)indexOf:返回字符串中第一个查找到的下标index,从左边开始查找.

(10)italics:使字体成为斜体字,与...标签结果相同.

(11)lastIndexOf:返回字符串中第一个查找到的下标index,从右边开始查找.

(12)length:返回字符串的长度.(不用带括号)

(13)link:产生一个超级链接,相当于设定的URL地址.

(14)small:将字体减小一号,与...标签结果相同.

(15)strike:在文本的中间加一条横线,与...标签结果相同.

(16)sub:显示字符串为下标字(subscript).

(17)substring:返回字符串中指定的几个字符.

(18)sup:显示字符串为上标字(superscript).

(19)toLowerCase:将字符串转换为小写.

(20)toUpperCase:将字符串转换为大写.

---