### 数据库相关

 1. Mogo查询:`db.getCollection('newlog').find({'message.core': /chat/})`
 2. mongod install:https://docs.mongodb.com/tutorials/install-mongodb-on-ubuntu/
 3. 启动mongodb: sudo service mongod start
 4. 安装elasticsearch：
 >安装java 8环境<br>
 >\$ wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.5.1.zip<br>
 >\$ unzip elasticsearch-5.5.1.zip<br>
 >\$ cd elasticsearch-5.5.1/<br>
 >\$ ./bin/elasticsearch#启动<br>
 >参考链接：<br>http://www.ruanyifeng.com/blog/2017/08/elasticsearch.html