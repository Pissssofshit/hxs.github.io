

## 如何确定存活性
可达性~=存活性
## 标记-清理
## 三色抽象
### 黑=>灰=>白
灰色：从栈或数据段上能追踪到的，遍历的根节点，包括栈上的和堆上的
黑色：已结束遍历的节点
白色：当不存在灰色对象时，此时剩下的白色对象就是垃圾

## STW

## 强三色不变式
黑色对象不能有对白色对象的引用
白色指针对黑色对象的写入操作，插入
## 弱三色不变式
黑色可以在有灰色对象可以抵达白色对象是有对白色对象的引用


## 写屏障
把对数据对象的修改通知到垃圾回收器
记录集：
### 插入写屏障
强三色不变式关注的是:关注白色指针到黑色对象的写入操作
可以将写入的白色对象着色为灰色，也可以将黑色对象改为灰色
### 删除写屏障
弱三色不变时 ：关注对那些到白色对象路径的破坏行为，例如在删除灰色对象对白色对象的引用时，可以将白色对象着色为灰色
### 读屏障
保证用户程序不会访问到已经存在新副本的陈旧对象

# 追踪式回收
## 内存碎片化
### 标记整理算法
清除完之后移动
### 复制式回收
#### 分代回收
弱分代假说：大部分对象都在年轻时死亡

# 引用计数
消耗分配到每一次操作，问题是循环引用



## 多核场景
TODO

## 内存泄露

* 子字符串造成的暂时性内存泄露
* 因为协程被永久阻塞而造成的永久性内存泄露
* 因为没有停止不再使用的time.Ticker值而造成的永久性内存泄露
当一个time.Timer值不再被使用，一段时间后它将被自动垃圾回收掉。 但对于一个不再使用的time.Ticker值，我们必须调用它的Stop方法结束它，否则它将永远不会得到回收。