## 键值对数据库是怎么实现的？
Redis 的键值对中的 key 就是字符串对象，而 value 可以是字符串对象，也可以是集合数据类型的对象，比如 List 对象、Hash 对象、Set 对象和 Zset 对象。

Redis 是使用了一个「哈希表」保存所有键值对，哈希表的最大好处就是让我们可以用 O(1) 的时间复杂度来快速查找到键值对。哈希表其实就是一个数组，数组中的元素叫做哈希桶


## 面试题
- [ ] Redis 持久化机制
- [ ] Redis 为什么这么快
### 资料
[Redis为什么这么快？](https://mp.weixin.qq.com/s/KtzvawDnQQwhfjnCoXpcMQ)
缓存雪崩、缓存穿透、缓存预热、缓存更新、缓存降级等问题
热点数据和冷数据是什么
Memcache与Redis的区别都有哪些？
单线程的redis为什么这么快
redis的数据类型，以及每种数据类型的使用场景，Redis 内部结构
redis的过期策略以及内存淘汰机制【～】
Redis 为什么是单线程的，优点
如何解决redis的并发竞争key问题
Redis 集群方案应该怎么做？都有哪些方案？
有没有尝试进行多机redis 的部署？如何保证数据一致的？
对于大量的请求怎么样处理
Redis 常见性能问题和解决方案？
讲解下Redis线程模型
为什么Redis的操作是原子性的，怎么保证原子性的？
Redis事务
Redis实现分布式锁