## TCP connect()扫描原理

TCP connect()扫描原理是：扫描主机通过TCP/IP协议的三次握手与目标主机的指定端口建立一次完整的连接。连接由系统调用connect开始。如果端口开放，则连接将建立成功；否则，若返回-1则表示端口关闭。

###### (1）sock模块:

 socket.gethostbyname(hostname):将主机名转换成IP地址返回

socket.gethostbyaddr(ip_address):传入一个Ip地址返回一个元组，其中包括主机名，别名列表和同一接口的Ip地址列表 socket.socket():创建一个socket

socket. connect(address,timeout,source_address):传入Ip地址和端口号返回一个socket对象，可以设置超时重连的时间

socket.send(data):项目地主机端口发送数据 socket.recv(size):从socket中接受size大小的字节数据

###### （2）threading模块：

threading.Semaphore(value=num):创建信号量为num的锁

threading.acquire():加锁

threading.release():解锁，释放信号量

多线程在速度上有明显优势，但是端口回显的信息可能是无序的，必须在同一时间内只有一个打印信息的函数，但是访问端口的却可以是多个的，同时还要避免重复访问同一个端口，造成资源浪费。因此，必须使用信号量加锁使用acquire()加锁，新好像允许信号运行，如果锁定了必须要等到信号量的进程释放锁，利用信号量可以保证在同



###### （3）实验结果

扫描手机端口的结果

![image-20200413231956534](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200413231956534.png)

扫描百度ip的结果

![image-20200413232220089](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200413232220089.png)

###### （4）对结果的评价

因为太多的端口关闭，所以就只显示了打开的端口，关闭的端口没让显示出来，因为只有几个端口打开我感觉结果好像是不太正确。

