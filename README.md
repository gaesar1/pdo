# PDO封装方法

更新到了微擎最新1.7,使用方法与微擎一样,不过调用方式采用的是命名空间的方法.

## 安装方法

`composer require logoove/pdo`

## 使用方法
~~~
use logoove\pdo\Pdo;
$db = new Pdo('localhost','root','111','3306','tp','oauth_');//主机地址,数据库帐号,密码,端口,表名,表前缀
var_dump($db->get('users'));//查询一条数据
$db->debug();//显示调试语句
~~~
## 更多介绍
~~~
表名 
$db->tablename('mc_members')
查询一条数据
$db->get('yoby_demo',['id'=>1]);
$db->get('yoby_demo',['id'=>1],['title','num']);返回特定字段
$db->get('yoby_demo',[],['count(*) as z','title','num','max(num)']);
$db->fetch("SELECT username, uid FROM ".tablename('users')." WHERE uid = :uid LIMIT 1", array(':uid' => 1));
查询单字段
$db->getcolumn('yoby_demo',['id'=>1],'title');
$db->fetchcolumn("SELECT COUNT(*) FROM ".tablename('users'));
查询多条记录
表名,条件,返回字段,主键,排序,限制条数
$db->getall('yoby_demo',[],[],'','id desc','LIMIT '.($pindex-1)* $psize.','.$psize); 
$db->fetchall("SELECT username, uid FROM ".tablename('users'), []);
插入数据,第二个参数数组
$db->insert('yoby_demo',[]);
$id = $db->insertid();插入id
修改
$db->update('yoby_demo',['num +='=>1],['id'=>1]);
删除
$db->delete('yoby_demo',['id'=>1]);
执行sql
$db->query("DELETE FROM ".tablename('users')." WHERE uid = :uid", array(':uid' => 2));
支持多条sql用分号隔开
$db->run($sql);
显示调试语句
$db->debug();
检测某个字段是否存在
$db->fieldexists('shopping_goods', 'credit');
检测某个表是否存在
$db->tableexists($tablename)
检测表是否为空
$db->exists($tb)
获取数据条数
$db->count($tb,['id'=>1])
~~~
