# 个人框架构想

- ~~mybatis xml 文件内使用java 枚举类 （决定是否使用mybatic后解决问题）~~
- JavaScript 文件版本号自动生成（哈希文件生成）  可选技术 [Gulp](http://www.gulpjs.com.cn/)  [实例](http://www.cnblogs.com/kevinCoder/p/5502395.html)
- __JRebel__ 配置文件 `rebel.xml` 加入 代码版本控制软件（`git` ， `svn`） ignore文件内，由开发人员自己维护
- 配置组，实现配置快速切换
- SQL目录，记录数据库结构变化，命名需按 `表名 + 时间(yyyy-MM-dd) + 动作(alert create ...)` 命名,数据库记录已执行SQL文件，在程序启动时检查出未执行文件并执行
- SQL缓存目录，使用ignore将目录内所有文件ignore，不允许提交，在代码发布时由管理人员统一为一个文件放到SQL目录内
- 支持消息队列(`rabbitmq`)
- 使用`docker`部署开发环境
