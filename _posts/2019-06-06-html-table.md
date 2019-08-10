---
layout: post
title: html表格
tags: html
categories: Front-End
---

### HTML`table`元素

1. `<th>` 表示标题单元格 (table header)
2. `<tr>` 表示行 (table row)
3. `<caption>` 对表格的描述.
4. `<th>` 中的scope属性，值可以是:row,col,rowgroup,colgroup.
5. `<td>` 数据单元格(table data)
6. `<thead>` 表格头部
7. `<tbody>` 表格主体
8. `<tfoot>` 表格尾部
9. 只能有一个`<thead>`,`<tfoot>`. 
10. 可以有多个`<tbody>`

~~~html
<table>
    <caption>澳柯玛净水器<caption>
    <thead>
        <tr>
          <th scope="col">型号</th>
          <th scope="col">净水流量(L/h)</th>
          <th scope="col">额定总净水量(L)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <td>ARB-32B2</td>
          <td>11.6</td>
          <td>1900</td>
        </tr>
        <tr>
          <td>ARB-31W6</td>
          <td>7.8</td>
          <td>1800</td>
        </tr>
        <tr>
          <td>ARB-32H5</td>
          <td>11.4</td>
          <td>1900</td>
        </tr>
        <tr>
          <td>ARB-35W3</td>
          <td>60</td>
          <td>2100</td>
        </tr>
        <tr>
          <td>ARB-35A1</td>
          <td>62.4</td>
          <td>8000</td>
        </tr>
    </tbody>
</table>
~~~

<table>
    <caption>澳柯玛净水器<caption>
    <thead>
        <tr>
          <th scope="col">型号</th>
          <th scope="col">净水流量(L/h)</th>
          <th scope="col">额定总净水量(L)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <td>ARB-32B2</td>
          <td>11.6</td>
          <td>1900</td>
        </tr>
        <tr>
          <td>ARB-31W6</td>
          <td>7.8</td>
          <td>1800</td>
        </tr>
        <tr>
          <td>ARB-32H5</td>
          <td>11.4</td>
          <td>1900</td>
        </tr>
        <tr>
          <td>ARB-35W3</td>
          <td>60</td>
          <td>2100</td>
        </tr>
        <tr>
          <td>ARB-35A1</td>
          <td>62.4</td>
          <td>8000</td>
        </tr>
    </tbody>
</table>
