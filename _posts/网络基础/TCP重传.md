## TCP重传
### 是什么
丢失时重新传数据包
### 为什么

### 怎么做
#### 超时重传
##### RTT(Round-Trip Time)
**RTT** 指的是数据发送时刻到接收到确认的时刻的差值，也就是包的往返时间
**RTO** 指的是Retransmission Timeout 超时重传时间
如果RTO较短，可能在数据包正常往返之前就进行了重传，会导致网络符合增大
如果RTO较大，重发就会慢，丢包发生半天才会重发，没有效率，性能查.
###### 如何测量RTO值
在理想情况下**超时重传时间 RTO 的值应该略大于报文往返 RTT 的值**

**采样**: 需要 TCP 通过采样 RTT 的时间，然后进行加权平均，算出一个平滑 RTT 的值，而且这个值还是要不断变化的，因为网络状况不断地变化。
除了采样 RTT，还要采样 RTT 的波动范围，这样就避免如果 RTT 有一个大的波动的话，很难被发现的情况

也就是**每当遇到一次超时重传的时候，都会将下一次超时时间间隔设为先前值的两倍。两次超时，就说明网络环境差，不宜频繁反复发送。**

超时触发重传存在的问题是，超时周期可能相对较长

#### 快速重传
TCP 还有另外一种**快速重传（Fast Retransmit）机制，它不以时间为驱动，而是以数据驱动重传。**

##### SACK方法
这种方式需要在 TCP 头部「选项」字段里加一个 SACK 的东西，它可以将**缓存的地图**发送给发送方，这样发送方就可以知道哪些数据收到了，哪些数据没收到，知道了这些信息，就可以只重传丢失的数据。
