MongoDB
====================

### 安装
* for mac 使用brew
  - brew update
  - brew install mongodb
  - mongod —config /usr/local/etc/mongod.conf
  - mongo

### 命令
    // db
    show dbs
    use testDb
    db.createCollection('testTb')
    show collections
    db.collections.count()
    // tb
    db.testTb.insert({name:'zhangsan', age:20, sex: 1, group:1})
    db.testTb.insert({name:'lisi', age:25, sex: 0, group:2})
    db.testTb.insert({name:'wangwu', age:20, sex: 1, group:3})
    db.testTb.insert({name:'zhaoliu', age:26, sex: 1, group:3})
    db.testTb.insert({name:'laoqi', age:20, sex: 1, group:1})
    // query
    db.testTb.find({_id:ObjectId('xxxx')})
    db.testTb.find({'name':'lisi'})
    db.testTb.find({'name':/zh*/i})
    db.testTb.findOne({'age':20})    
    db.testTb.find({}, {'name':1, 'age':1})   // 指定返回的键
    db.testTb.find({'age':{$gt:20, $lt:30}})  // $ltg 小于等于；$gte 大于等于；$ne 不等于
    db.testTb.find({'name':{$in:['zhangsan', 'lisi']}});  // in
    db.testTb.find({'name':{$nin:['zhangsan', 'lisi']}}); // not in
    db.testTb.find({'$or':[{'name':'zhangsan'}, {'age':25}]}) // or
    db.testTb.find().sort({age:-1}).limit(3).skip(1)   // sort, limit and skip
    db.testTb.find().pretty()  // 格式
    // update
    var zs = db.testTb.findOne({name:'zhangsan'});
    zs.age = 22;
    db.testTb.update({name:'zhangsan'}, zs) || db.testTb.save(sz)
    
    db.testTb.update({name:'zhangsan'}, {$inc:{age:1}});
    
    db.testTb.update({name:'zhangsan'}, {$set:{age:21}})
    db.testTb.update({name:'zhangsan'}, {$set:{test:1}})
    db.testTb.update({name:'zhangsan'}, {$unset:{test:1}})
    db.testTb.update({name:'zhangsan'}, {$set:{email:['zhangsan@qq.com']}})
    db.testTb.update({name:'zhangsan'},{$push:{email:'zhangsan1@qq.com'}})
    db.testTb.update({name:'zhangsan'},{$addToSet:{email:'zhangsan1@qq.com'}}) // 避免重复
    db.testTb.update({name:'bob'}, {$inc:{visit:1}}, true) // 如果不存在，则创建，第三个参数
    db.testTb.update({}, {$set:{sex:0}}, false, true)  // 批量更新，第4个参数
    // delete
    db.testTb.remove()
    // shell
    var cursor = db.testTb.find()
    cursor.forEach(function(x){print(x.name)})
    

### 故障解决
* Unable to create/open lock file: /data/mongod.lock errno:13 Permission denied
  - sudo chown -R username /data/db

### PHP MongoDB
* 安装 @TODO
* 连接数据库
  - $conn = new MongoClient();
  - $conn = new MongoClient( "mongodb://localhost:27017" );
  - $conn = new MongoClient( "mongodb://localhost", array('username'=> $username, 'password'=>$password) );
* 获取实例
  - $db = $conn->dbname;
* 获取集合
  - $collection = $db->collectionName;
* 插入文档
  - $collection->insert( array() );
* 计算文档数量
  - $collection->count();
* 游标
  - $cursor = $collection->find();
  - foreach ($cursor as $id => $value) {}
* 查询条件
  - $query = array('age' => array('$gt' => 15, '$lt' => 30));  // >15 and < 30
  - $cursor = $collection->find( $query );
  - while ($cursor->hasNext()) {
        var_dump($cursor->getNext());
    } 
* 更新
  - $db->collection->update(array('b'=>'q'), array('$set'=>array()));
* 删除
  - $db->collection->remove(array());
* 排序
  - $db->collection->find(array())->sort(array('name'=>1));
* limit
  - $db->collection->find()->limit(10)->skip(20);  // limit 20, 10


### 相关书籍

[《MongoDB权威指南》](http://book.douban.com/subject/6068947/)

[《深入学习MongoDB》](http://book.douban.com/subject/10439364/)


* 《MongoDB权威指南》
* 《深入学习MongoDB》

### 相关工具
[robomongo](http://www.robomongo.org/)

