MongoDB
====================

## 安装
* for mac 使用brew
  - brew update
  - brew install mongodb
  - mongod -config /usr/local/etc/mongod.conf
  - mongo

## 命令

#### 数据库
    db.hostInfo()  //
    show dbs
    use [dbName]
    db.dropDatabase()  // 删除当前数据库
   
#### 集合 
    db.createCollection([collectionName])
    show collections
    db.[collectionName].remove()   // 删除集合中的文档，但保留索引
    db.[collectionName].remove({key:value})   // 删除集合中的文档，但保留索引
    db.[collectionName].count({key:value})
    db.[collectionName].drop()

#### 插入
    db.[collectionName].insert({key:value})
    var o = {a:1, b:2}; db.[collectionName].save(o)
   
#### 查询
    db.[collectionName].find()
    db.[collectionName].find({key:value})
    db.getCollection([collectionName]).find({})
    db.[collectionName].find({}, {key1:1, key2:1})  // 指定返回的键
    db.[collectionName].find({key:{$gt:20, $lt:30}}) // 条件查询；$ltg 小于等于；$gte 大于等于；$ne 不等于
    db.[collectionName].find({key:{$in:[value1, value2]}});  // $in | $nin
    db.[collectionName].find({key:{$or:[{key1:value1}, {key2:value2}]}}); // or
    // sort, limit, skip
    db.[collectionName].find().sort({key1:-1}).limit(20).skip(1)
    db.[collectionName].find().pretty()  // 格式
   
#### 更新
    db.[collectionName].update({key:value}, {$set:{key1:value1}})
    db.[collectionName].update({key:value}, {$unset:{key1:1}})
    db.[collectionName].update({key:value}, {$set:{key1:value1}}, false, true)  // 第4个参数，批量更新
    db.[collectionName].update({key:value}, {$inc:{key1:n}})
    db.[collectionName].update({key:value}, {$push:{key1:value1]})
    db.[collectionName].update({key:value}, {$pop:{key1:value1]})
    db.[collectionName].update({key:value}, {$addToSet:{key1:value1]})
    
#### 删除
    db.[collectionName].remove({key:value})

#### distinct、group、mapreduce
    db.runCommand({"distinct":"[collectionName]", "key":"[key]"})
    // @TODO

## Testing
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
    db.testTb.find({}, {'name':1, 'age':1})   
    db.testTb.find({'age':{$gt:20, $lt:30}})  
    db.testTb.find({'name':{$in:['zhangsan', 'lisi']}});  
    db.testTb.find({'name':{$nin:['zhangsan', 'lisi']}}); 
    db.testTb.find({'$or':[{'name':'zhangsan'}, {'age':25}]})  
    db.testTb.find().sort({age:-1}).limit(3).skip(1)               
    db.testTb.find().pretty()   
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
    db.testTb.update({name:'zhangsan'},{$addToSet:{email:'zhangsan1@qq.com'}}) 
    db.testTb.update({name:'bob'}, {$inc:{visit:1}}, true)     db.testTb.update({}, {$set:{sex:0}}, false, true)  
    // delete
    db.testTb.remove()
    db.testTb.drop()
    // shell
    var cursor = db.testTb.find()
    cursor.forEach(function(x){print(x.name)})
    // 数据库所有命令list
    db.listCommands()
   
#### 安全和认证
* @TODO   
   
 
## 故障解决
* Unable to create/open lock file: /data/mongod.lock errno:13 Permission denied
  - sudo chown -R username /data/db

## PHP MongoDB
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


### 相关资料
[官网](https://www.mongodb.org/)

[robomongo工具](http://www.robomongo.org/)

