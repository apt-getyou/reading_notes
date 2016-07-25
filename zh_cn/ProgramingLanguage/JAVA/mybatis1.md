# mybatis在xml文件中处理大于号小于号的方法

[转载](http://4925054.blog.51cto.com/4915054/1720131)

--------------------------------

第一种方法：
用了转义字符把>和<替换掉，然后就没有问题了。
SELECT * FROM test WHERE 1 = 1 AND start_date  &lt;= CURRENT_DATE AND end_date &gt;= CURRENT_DATE

附：XML转义字符

| 转义字符 | 原字符 | 中文含义 |
|:---:|:-----:|:-----:|
|  `&lt;` | `<` | 小于号|




第二种方法：
因为这个是xml格式的，所以不允许出现类似“>”这样的字符，但是都可以使用<![CDATA[ ]]>符号进行说明，将此类符号不进行解析
你的可以写成这个：
mapper文件示例代码
```SQL
<![CDATA[ when min(starttime)<='12:00' and max(endtime)<='12:00' ]]>  
```
