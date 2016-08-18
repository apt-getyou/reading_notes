```SQL
-- test table:    
CREATE TABLE IF NOT EXISTS card (  
  cardno int(10)  not null PRIMARY KEY,  
  cardnum int(10) not null   
)engine=innodb default charset=utf8 ;
```  
普通的 INSERT INTO 插入：
```SQL
INSERT INTO card(cardno, cardnum) VALUES('1111', '100');

INSERT INTO card(cardno, cardnum) VALUES('2222', '200');
```

对于普通的 INSERT 插入，如果想要保证不插入重复记录，我们只有对某个字段创建唯一约束实现（比如：cardno卡号不能重复）；

那有没有不创建唯一约束，仅通过 INSERT INTO 一条语句实现的方案呢？

答案：有的， INSERT INTO IF EXISTS 具体语法如下：
```SQL
INSERT INTO table (field1, field2, fieldn)
  SELECT
    'field1',
    'field2',
    'fieldn'
  FROM DUAL
  WHERE NOT EXISTS(SELECT field
                   FROM table
                   WHERE field = ?)
```
其中的 DUAL 是一个临时表，不需要物理创建，这么用即可。
针对上面的card示例的改造如下：
```SQL
INSERT INTO card (cardno, cardnum)
SELECT
  '111',
  '100'
FROM DUAL
WHERE NOT EXISTS(SELECT cardno
                FROM card
                WHERE cardno = '111');
INSERT INTO card (cardno, cardnum)
SELECT
  '222',
  '200'
FROM DUAL
WHERE NOT EXISTS(SELECT cardno
                FROM card
                WHERE cardno = '222');
```

搞定！


[原文地址](http://blog.csdn.net/pandajava/article/details/45667001) 转载请注明。
