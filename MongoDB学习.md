# MOongoDB学习记录

## 数据库基本操作
* 创建/切换数据库 use DATABASE_NAME
* 查看所有数据库 show dbs
* 删除数据库 db.dropDatabase()
* 删除集合db.collection.drop() 其中collection为集合的table
* 插入文档 db.COLLECTION_NAME.insert(document) 其中NAME为集合名
* 查看集合 db.COLLECTION_NAME.find()
* db.collection.insertOne():向指定集合中插入一条文档数据
* db.collection.insertMany():向指定集合中插入多条文档数据
``` javascript
#  插入单条数据
> var document = db.collection.insertOne({"a": 3})
> document
{
        "acknowledged" : true,
        "insertedId" : ObjectId("571a218011a82a1d94c02333")
}

#  插入多条数据
> var res = db.collection.insertMany([{"b": 3}, {'c': 4}])
> res
{
        "acknowledged" : true,
        "insertedIds" : [
                ObjectId("571a22a911a82a1d94c02337"),
                ObjectId("571a22a911a82a1d94c02338")
        ]
}
```
* 更新文档 
``` javascript
db.collection.update(
   <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>
   }
)
# query : update的查询条件，类似sql update查询内where后面的。
# update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
# upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
# multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
# writeConcern :可选，抛出异常的级别 
例： db.col.update({'title':'MongoDB 教程'},{$set:{'title':'MongoDB'}})
可以看到标题(title)由原来的 "MongoDB 教程" 更新为了 "MongoDB"。
以上语句只会修改第一条发现的文档，如果你要修改多条相同的文档，则需要设置 multi 参数为 true。
>db.col.update({'title':'MongoDB 教程'},{$set:{'title':'MongoDB'}},{multi:true})
```
* 替换文档

save() 方法通过传入的文档来替换已有文档。语法格式如下：
``` javascript
db.collection.save(
   <document>,
   {
     writeConcern: <document>
   }
)
# document : 文档数据。
# writeConcern :可选，抛出异常的级别。
```
