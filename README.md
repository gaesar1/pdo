# pdo
更新到了最新1.7

- 微擎的数据库操作类提取

~~~
表名 
tablename('mc_members')
查询一条数据
pdo_get('yoby_demo',['id'=>1]);
pdo_get('yoby_demo',['id'=>1],['title','num']);返回特定字段
pdo_get('yoby_demo',[],['count(*) as z','title','num','max(num)']);
pdo_fetch("SELECT username, uid FROM ".tablename('users')." WHERE uid = :uid LIMIT 1", array(':uid' => 1));
查询单字段
pdo_getcolumn('yoby_demo',['id'=>1],'title');
pdo_fetchcolumn("SELECT COUNT(*) FROM ".tablename('users'));
查询多条记录
表名,条件,返回字段,主键,排序,限制条数
pdo_getall('yoby_demo',[],[],'','id desc','LIMIT '.($pindex-1)* $psize.','.$psize); 
pdo_fetchall("SELECT username, uid FROM ".tablename('users'), []);
插入数据,第二个参数数组
pdo_insert('yoby_demo',[]);
$id = pdo_insertid();插入id
修改
pdo_update('yoby_demo',['num +='=>1],['id'=>1]);
删除
pdo_delete('yoby_demo',['id'=>1]);
执行sql
pdo_query("DELETE FROM ".tablename('users')." WHERE uid = :uid", array(':uid' => 2));
支持多条sql用分号隔开
pdo_run($sql);
显示调试语句
pdo_debug();
检测某个字段是否存在
pdo_fieldexists('shopping_goods', 'credit');
检测某个表是否存在
pdo_tableexists($tablename)
~~~
