[toc]

## slice和数组的区别
数组是一段连续的内存空间
切片是基于数组包装的一个数据结构
## slice类型基本结构
data：元素存哪里
len：存了多少个元素
cap：可以存多少个元素

### 底层数组
切片可以基于数组构造
比如
```
arr := [10]int{0,1,2,3,4,5,6,7,8,9}
```
变量arr是容量为10的整型数组（注意数组容量声明了就不能变了）。我们可以把不同的slice关联到同一个数组，如下代码所示：
```
var s1 []int = arr[1:4] // 左闭右开
var s2 []int = arr[7:]
```
s1和s2会公用底层数组arr,
注意,s1的len是3，长度(可以容纳的元素个数)是9，这是基于底层数组的长度决定的
s2的len是3，长度也是3
## 扩容规则
s2的容量已经达到了上限，如果再继续append，原先的底层数组就不能再使用了，需要开辟一个新数组。这里就涉及到了扩容规则。


### 1.15