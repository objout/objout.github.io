---
layout: post
title: Tips for Google Chrome
tags: browser
categories: Front-End
---

## 1.快速切换文件

`Ctrl + p` 

可以快速搜寻和打开你项目的文件.


## 2.在源代码中搜索

`Ctrl + Shift + F`

这种搜索方式还支持正则表达式.


## 3.快速跳转到指定行

`Ctrl + G`

在source标签中打开一个文件进行跳转.

另外一种方式是按`Ctrl + O`,输入:和行数,而不用去寻找一个文件.

## 4.在控制台选择元素

DevTools控制台支持一些变量和函数来选择DOM元素:

(1)$()–document.querySelector()的简写,返回第一个和css选择器匹配的元素.例如$(‘div’)返回这个页面中第一个div元素

(2)$$()–document.querySelectorAll()的简写,返回一个和css选择器匹配的元素数组.

(3)$0-$4–依次返回五个最近你在元素面板选择过的DOM元素的历史记录,$0是最新的记录,以此类推.


## 5.使用多个插入符进行选择

`Ctrl + Click`

在要编辑的地方Click,作用是一次在多个地方编辑.


## 6.保存记录

勾选在Console标签下的保存记录选项,可以使console继续保存记录而不会在每个页面加载之后清除记录.当你想要研究在页面还没加载完之前出现的bug时,这会是一个很方便的方法.


## 7.优质打印

Chrome’s Developer Tools有内建的美化代码,可以返回一段最小化且格式易读的代码.Pretty Print的按钮在Sources标签的左下角.


## 8.设备模式

支持移动端.


## 9.设备传感与仿真

设备模式的另一个功能是模拟移动设备的传感器,例如触摸屏幕和加速计.你甚至可以恶搞你的地理位置.这个功能位于元素标签的底部,点击“show drawer”按钮,就可看见 Emulation标签-->Sensors.


## 10.颜色选择器

当在样式编辑中选择了一个颜色属性时,你可以点击颜色预览,就会弹出一个颜色选择器.当选择器开启时,如果你停留在页面,鼠标指针会变成一个放大镜,让你去选择像素精度的颜色.


## 11.强制改变元素状态

DevTools有一个可以模拟CSS状态的功能,例如元素的hover和focus,可以很容易的改变元素样式.在CSS编辑器中可以利用这个功能


## 12.可视化的DOM阴影

Web浏览器在构建如文本框、按钮和输入框一类元素时,其它基本元素的视图是隐藏的.不过,你可以在Settings-->General中切换成Show user agent shadow DOM,这样就会在元素标签页中显示被隐藏的代码.甚至还能单独设计他们的样式,这给你了很大的控制权.


## 13.选择下一个匹配项

`Ctrl + D`

当前选中的词的下一个匹配也会被选中,有利于同时对它们进行编辑.


## 14.改变颜色格式

在颜色预览功能使用`Shift + Click`

可以在rgba、hsl和hexadecimal来回切换颜色的格式


## 15.通过workspaces编辑本地文件

Workspaces是Chrome DevTools的一个强大功能，这使DevTools变成了一个真正的IDE。Workspaces会将Sources选项卡中的文件和本地项目中的文件进行匹配，所以你可以直接编辑和保存，而不必复制/粘贴外部改变的文件到编辑器。


为了配置Workspaces，只需打开Sources选项，然后右击左边面板的任何一个地方，选择 Add Folder To Worskpace，或者只是把你的整个工程文件夹拖放入Developer Tool。现在，无论在哪一个文件夹，被选中的文件夹，包括其子目录和所有文件都可以被编辑。为了让Workspaces更高效，你可以将页面中用到的文件映射到相应的文件夹，允许在线编辑和简单的保存。

<a href="https://www.w3cschool.cn/chromedevtools/ntao1oeh.html">
	Link</a>