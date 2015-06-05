### 连接数据库    
    $conn = new MongoClient();
    $conn = new MongoClient( "mongodb://localhost:27017" );
    $conn = new MongoClient( "mongodb://localhost", array('username'=> $username, 'password'=>$password) );

### 获取实例
    $db = $conn->dbname;

### 获取集合
    $collection = $db->collectionName;

### 插入文档
    $collection->insert( array() );

### 计算文档数量
    $collection->count();

### 游标
    $cursor = $collection->find();
    foreach ($cursor as $id => $value) {}

### 查询条件
    $query = array('age' => array('$gt' => 15, '$lt' => 30));  // >15 and < 30
    $cursor = $collection->find( $query );
    while ($cursor->hasNext()) {
        var_dump($cursor->getNext());
    } 
    
### 更新
    $db->collection->update(array('b'=>'q'), array('$set'=>array()));

### 删除
    $db->collection->remove(array());

### 排序
    $db->collection->find(array())->sort(array('name'=>1));

### limit
    $db->collection->find()->limit(10)->skip(20);  // limit 20, 10

