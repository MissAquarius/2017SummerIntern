## 1.定义
* redis是一个开源的、支持网络、可基于内存亦可持久化的日志型 、Key-Value数据库，并提供多种语言的API
  * 日志型：append only，所有写操作只追加不修改老数据，数据文件以日志型只增不减的写入。
  对文件大小有限制，当文件大小达到限制时，生成一个新的文件，老的文件(older data file)只读不写，因而在任意一个时间点只有一个文件是可写的(active data file).
* 它有三个主要使其有别于其它很多竞争对手的特点：
  *	Redis是完全在内存中保存数据的数据库，使用磁盘只是为了持久性目的； 
  * Redis相比许多键值数据存储系统有相对丰富的数据类型 ； 
  *	Redis可以将数据复制到任意数量的从服务器中；
## 2.优缺点
* 优点：
  *	读取快速；
  *	数据类型丰富；
  *	原子性操作 ；
  * MultiUtility工具
* 缺点：
  *	断电或重启可能会丢失数据
## 3.命令总结
* 连接服务：
  * 本地：redis-cli
  * 远程：redis-cli –h host –p port –a password
* 字符串string操作：
  * 创建key，并赋值：set key-name key-value     备注：若key已存其他值，set会写旧值，且无视类型
  * 查看key的值，若存在，返回值，不存在，返回nil：get key-name
  * 获取子串：getrange key-name start end  
    * 老版本叫做substr用法同getrange。
    * 字符串的截取范围由 start 和 end 两个偏移量决定(包括 start 和 end 在内)。
  *	修改key的值，并且同时返回key的旧值，若key不存在,则创建key并赋值，返回nil：getset key-name new-key-value
  * 设置多个key的值，对应分别显示：mset key1 key2 key3…
  * 查看多个key的值，对应分别显示：mget key1 key2 key3…
    * 备注：多个key-name之间没有逗号
  * 为指定的key设置值及过期时间：setex key-name time-out key-value
  * 设置完之后就开始计时，要查看键到期的剩余时间：ttl key-name
  * 创建key的时候，只有key-name不存在的时候才创建：setnx key-name key-value 创建成功，返回1，不成功，返回0
  * 用给定的字符串覆盖key所存储的字符串值，覆盖的位置从偏移量offset开始：setrange key-name offset key-value
  * 求字符串长度：strlen key-name
  * 将字符串存储的数字加上一个增量：incrby key-name incr_amount
                            Incrbyfloat  key-name inc_amount
    * 若字符串不可加，返回错误提示；若key-name不存在，则创建并初始化为0;
    * 浮点类型的数，会自动略去无意义的0
  * 将字符串存储的数字减去一个数值：decrby key-name decr_amount
    * 若字符串不可减，返回错误提示；若key-name不存在，则创建并初始化为0
  * 为指定的key追加值：append key-name key-value
    * 若key-name不存在，这条命令与set key-name key-value效果一样




    




