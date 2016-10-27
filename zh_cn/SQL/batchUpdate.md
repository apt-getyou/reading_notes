# 数据库批量更新方法及对应效率

date : 2016.10.08  16:52

---------------------
> 本篇文章以Mysql为环境进行实践,使用php生成SQL语句
> 其中 使用  [illuminate/database](https://github.com/illuminate/database) 实现数据库对接，使用[fzaninotto/Faker](https://github.com/fzaninotto/Faker) 制造数据库数据
> 在mysql环境下，通过SQL实现批量更新的方法有三种   

1. 普通方式，直接使用update语句更新，即有多少需要更新的数据就写多少条语句执行
