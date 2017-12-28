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
* 替换文档<br />
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
* 删除文档
``` 
db.collection.remove(
   <query>,
   {
     justOne: <boolean>,
     writeConcern: <document>
   }
)
# query :（可选）删除的文档的条件。
# justOne : （可选）如果设为 true 或 1，则只删除一个文档。
# writeConcern :（可选）抛出异常的级别。
```
删除所有数据`db.col.remove({})`
* 查询文档<br />
`db.collection.find(query, projection)`
>query ：可选，使用查询操作符指定查询条件<br />
>projection ：可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。

如果你需要以易读的方式来读取数据，可以使用 pretty() 方法，语法格式如下：<br />
`db.col.find().pretty()`
<table>
<thead>
<tr>
<th>操作</th>
<th>格式</th>
<th>范例</th>
<th>RDBMS中的类似语句</th>
</tr>
</thead>
<tbody>
<tr>
<td>等于</td>
<td><code>{&lt;key&gt;:&lt;value&gt;}</code></td>
<td><code>db.col.find({"by":"菜鸟教程"}).pretty()</code></td>
<td><code>where by = '菜鸟教程'</code></td>
</tr>
<tr>
<td>小于</td>
<td><code>{&lt;key&gt;:{$lt:&lt;value&gt;}}</code></td>
<td><code>db.col.find({"likes":{$lt:50}}).pretty()</code></td>
<td><code>where likes &lt; 50</code></td>
</tr>
<tr>
<td>小于或等于</td>
<td><code>{&lt;key&gt;:{$lte:&lt;value&gt;}}</code></td>
<td><code>db.col.find({"likes":{$lte:50}}).pretty()</code></td>
<td><code>where likes &lt;= 50</code></td>
</tr>
<tr>
<td>大于</td>
<td><code>{&lt;key&gt;:{$gt:&lt;value&gt;}}</code></td>
<td><code>db.col.find({"likes":{$gt:50}}).pretty()</code></td>
<td><code>where likes &gt; 50</code></td>
</tr>
<tr>
<td>大于或等于</td>
<td><code>{&lt;key&gt;:{$gte:&lt;value&gt;}}</code></td>
<td><code>db.col.find({"likes":{$gte:50}}).pretty()</code></td>
<td><code>where likes &gt;= 50</code></td>
</tr>
<tr>
<td>不等于</td>
<td><code>{&lt;key&gt;:{$ne:&lt;value&gt;}}</code></td>
<td><code>db.col.find({"likes":{$ne:50}}).pretty()</code></td>
<td><code>where likes != 50</code></td>
</tr>
</tbody>
</table>
<br/>
* MongoDB AND条件
MongoDB 的 find() 方法可以传入多个键(key)，每个键(key)以逗号隔开，即常规 SQL 的 AND 条件。
语法格式如下：

`db.collention.find({key1:value1. key2,value2}).pretty()`
* MongoDB OR条件
```
db.col.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```
* MongoDB $type操作符 <table class="reference">
<tbody>
<tr><th><strong>类型</strong></th>
<th><strong>数字</strong></th>
<th><strong>备注</strong></th>
</tr>
<tr class="row-even"><td>Double</td>
<td>1</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>String</td>
<td>2</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>Object</td>
<td>3</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>Array</td>
<td>4</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>Binary data</td>
<td>5</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>Undefined</td>
<td>6</td>
<td>已废弃。</td>
</tr>
<tr class="row-even"><td>Object id</td>
<td>7</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>Boolean</td>
<td>8</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>Date</td>
<td>9</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>Null</td>
<td>10</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>Regular Expression</td>
<td>11</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>JavaScript</td>
<td>13</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>Symbol</td>
<td>14</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>JavaScript (with scope)</td>
<td>15</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>32-bit integer</td>
<td>16</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>Timestamp</td>
<td>17</td>
<td>&nbsp;</td>
</tr>
<tr class="row-even"><td>64-bit integer</td>
<td>18</td>
<td>&nbsp;</td>
</tr>
<tr class="row-odd"><td>Min key</td>
<td>255</td>
<td>Query with <tt class="docutils literal"><span class="pre">-1</span></tt>.</td>
</tr>
<tr class="row-even"><td>Max key</td>
<td>127</td>
<td>&nbsp;</td>
</tr>
</tbody></table>







