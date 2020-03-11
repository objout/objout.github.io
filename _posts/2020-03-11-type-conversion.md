---
layout: post
title: 类型转换
tags: JavaScript
categories: Front-End
---

## 简述

大多数情况下,运算符和函数会自动将操作数的值转换为正确类型.

eg. `alert`会自动将任何值转换为字符串.

在某些情况下,需要进行显示转换.

## 字符串转换

需要字符串形式的值时,就会进行字符串转换.

可以显示调用`String(value)`进行转换.

```javascript
let value = true;
alert(typeof value); // boolean
value = String(value); // "true"
alert(typeof value); // string
```

## 数字型转换

在算数函数和表达式中会自动进行number类型转换.

```javascript
alert("6" / "2"); // 3 string -> number
```

`Number(value)`可以进行显示转换.

```javascript
let str = "123";
alert(typeof str); // string
let num = Number(str); // 123
alert(typeof num); // number
```

当从string类型源(文本表单)中读取值但期望输入一个数字通常需要显示转换.

若不能发生转换,返回`NaN`.

```javascript
let age = Number("hello world");
alert(age); // NaN
```

### number类型转换规则

- `undefined` -> `NaN`.
- `null` -> 0.
- `true` and `false` -> 1 and 0.
- `string` -> 去掉首尾空格后的纯数字字符串中含有的数字,若为空串,则结果为0,否则,将会从剩余字符串中读取数字,当类型转换出现错误返回`NaN`.

```javascript
console.log(Number("    123    ")); // 123
console.log(Number("123z")); // NaN
console.log(Number(true)); // 1
console.log(Number(false)); // 0
console.log(Number(undefined)); // NaN
```

## 布尔型转换

它发生在逻辑运算中,但是可以通过`Boolean(value)`显示转换.

- `0`, 空串, `null`, `undefined`, `NaN` -> `false`.
- other values -> `true`.

```javascript
console.log(Boolean("0")); // true
console.log(Boolean(" ")); // true
```

## 对象-原始值转换

对象到原始值的转换,是由许多期望以原始值作为值的内建函数和操作符自动调用的.

- 所有的对象在布尔上下文中均为`true`.所以对于对象,不存在布尔转换.
- 数值转换发生在对象相减或应用数学函数时.例如`Date`对象可以相减,`date1`-`date2`的结果是日期之间的差值.
- 字符串转换通常发生在像`alert(obj)`这样输出一个对象和类似的上下文中.

### ToPrimitive

可以使用特殊的对象方法,对字符串和数值转换进行微调.

下面是三个类型转换的变体,被称为"hint",在[规范](https://tc39.github.io/ecma262/#sec-toprimitive)中有详细介绍.
(当一个对象被用在需要原始值的上下文中式,对象会被转换为原始值):

1. `string`
    对象到字符串的转换.


```javascript
alert(obj);
anotherObj[obj] = 123;
```


2. `"number"`
    对象到数字的转换.


```javascript
// 显示转换
let num = Number(obj);
// 数学运算(处理二进制加法)
let n = +obj;
let delta = date1 - date2;

// 比较
let greater = user1 > user2;
```


3. `"default"`
    在少数情况下发生,当操作者"不确定"期望值的类型时.
	eg. 二元操作符`+`可用于字符串连接也能进行数字相加,所以字符串和数字类型都可以.
	因此,当二元加法得到对象类型的参数时,它依据"default" hint来进行转换.
	
	若对象被用于与字符串,数字或`symbol`进行`==`比较,使用"default" hint.
	
	
```javascript
let total = obj1 + obj2;
if (user == 1) {...}
```


像大于/小于比较运算符,也可以同时用于字符串和数字.它们使用"number" hint, 而不是"default"(历史原因).

除了一种情况(date 对象)之外,所有内建对象都以和"number"相同的方式实现"default"转换.

为了进行转换,JavaScript尝试查找并调用三个对象方法:

1. 调用`obj[Symbol.toPrimitive] (hint)`,一个带有symbol键`Symbol.toPrimitive`(系统symbol)的方法,若这个方法存在.
2. 否则,若hint是"string" - 尝试`obj.toString()`和`obj.valueOf()`,无论哪个存在.
3. 若是"number"或"default" - 尝试`obj.valueOf()`和`obj.valueOf()`,无论哪个存在.

### Symbol.toPrimitive

它被用来给转换方法命名:

```javascript
obj[Symbol.toPrimitive] = function (hint) {
	// 返回一个原始值
	// hint = "string", "number", "default"中的一个
};
```

```javascript
let user = {
	name: "John",
	money: 123,
	
	[Symbol.toPrimitive](hint) {
		alert(`hint: ${hint}`);
		return hint == "string" ? `{name: "$(this.name)"}` : this.money;
	}
};

// 转换演示
alert(user); // hint: string -> {name: 'John'}
alert(+user); // hint: number -> 1000
alert(user + 500); // hint: default -> 1500
// 根据转换的不同,user变成一个自描述字符串或者一个数字.
// 单个方法user[Symbol.toPrimitive]处理所有的转换情况.
```

### toString / valueOf

若没有`Symbol.toPremitive`,那么:
- "string" hint - `toString` -> `valueOf`
- other, `valueOf` -> `toString`.

```javascript
let user = { name: 'John' };
alert(user); // [object Object]
alert(user.valueOf() === user); // true
```

所以, 若将一个对象当作字符串使用,,默认情况下会看到`[object Object]`.

这里提到默认值`valueOf`只是为了完整起见,以避免混淆.它返回对象本身,因此被忽略.

```javascript
let user = {
	name: 'John',
	money: 100,
	
	// 对于 hint-"string"
	toString() {
		return `{name: "${this.name}"}`;
	},
	
	// 对于 "number" or "default"
	valueOf() {
		return this.money;
	}
};

alert(user); // toString
alert(+user); // valueOf
alert(user + 50); // valueOf\
```

通常我们希望有一个"全能"的地方来处理所有原始转换.在这种情况下,我们可以实现`toString`:

```javascript
let user = {
	name: "Safari",
	
	toString() {
		return this.name;
	}
};

alert(user); // toString -> John
alert(user + 500); // toString -> John500
// 若没有Symbol.toPrimitive和valueOf, toString处理所有原始转换
```

### 返回类型

关于所有原始的转换方法,有一个重要的点,就是它们不一定返回"hint"的原始值.

没有限制`toString()`是否返回字符串,或`Symbol.toPrimitive`方法是否为hint"number"返回数字.

唯一强制的是:这些方法必须返回一个原始值而不是对象.

历史的原因,若`toString`或`valueOf`返回了一个字符串,不会出现错误,但是这种值会被忽略.
这是因为在JavaScript发展的初期没有很好的错误的概念.

相反,`Symbol.toPrimitive`必须返回一个原始值,否则出现错误.


### 进一步的转换

若对象作为参数传递,则会出现两个阶段:
1. 对象被转换为原始值(通过前面描述的规则)
2. 若生成的原始值的类型不正确,就会继续进行转换.

```javascript
let obj = {
	// toString 在没有其它方法的情况下处理所有转换
	toString() {
		return "2";
	}
};

alert(obj * 2); // 4
```

```javascript
let obj = {
	toString() {
		return "2";
	}
};

alert(obj + 2); // "22"
```

在实践中,为了便于进行日志记录或调试,对于所有能够返回一种可读性好的对象的表达式进行转换,只实现以obj.toString()作为全部转换的方法就够了.
