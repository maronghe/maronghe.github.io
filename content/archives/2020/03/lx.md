项目启动

``````
main.go ->
1.初始化qLog （日志地址、队列大小、并发标识、最小日志级别）
2.init etcd
3. init infra-components ？
4.init project config（cmd -> etcd -> default）
	openHost、appHost、authHost
	app白名单（redirect、cors）
	
	init router -> pathPrefix/api/v1 和 allowOrigin （可信域名）
	init mongo、mysql、redis、crontab、openLog、s3等
	https 需要配置 tls证书和tls私钥 
``````











数据存储

``````
8 bit -> 1 byte (0xab) // 8位 = 1字节
short 16 bit -> 2 byte 
int 32 bite -> 4 byte
int64 64 bite -> 8 byte

``````







> 并发、并行

1. 单核CPU中每个任务通过时间片或主动让出执行权来实现业务切换。（并发）
2. 多核CPU在一个进程中使多个线程并行同时运行，达到并行。

>进程、线程、携程

1. 进程是操作系统的资源分配的基本单位，有独立运行空间。
2. 线程是CPU调度基本单位，线程依附于进程存在，并共享父进程的资源。
3. **协程是用户态的轻量级线程，协程的调度完全是用户控制**，其切换时不需要进入内核切换，所以无内核开销。

> 线程上下文切换

​	**上下文切换**代价是昂贵的，在CPU上交换线程会花费很多时间。延迟在50-100us之间，硬件平均在每个核心上执行是12op/us所以一次切换可能会花费600-1200指令延迟。

> 工作窃取

本地-> (为空时)全局-> 本地  ( WSS )

> 减少阻塞

1. 由于Atomic、Mutex、Channel等导致GoRoutine阻塞

   调度器把当前的G切换出去，重新安排LRQ的其他GoRoutine。

2. 由于网络请求或IO操作导致G阻塞。

   Go提供了NetPoller（网络轮询器）来处理网络请求和网络IO问题，通过epoll来实现多路复用。

   将G放入NetPoller队列中，避免创建新M，G再放回LRQ中等待执行。

3. syscall时（无法使用NetPoller）而进行系统调用的GoRoutine阻塞了当前的M

   1.13之前G和M会绑定（IO同步调用阻塞M），将M与P分离，同时也将G带走，然后调度器引入新的M2和来服务P，此时LRQ中继续执行G。阻塞后G1可以移回LRQ，M1以待重复使用。

4. GoRoutine执行Sleep导致M阻塞

   将G放入Timer等待队列中，继续执行LRQ的下一个G。等待执行契机放入LRQ执行。

   

