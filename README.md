# LinuxBenchmarking

### 磁盘读写
```
fio测试读写速度，需要安装：yum install fio -y
随机读：fio -filename=/home/data -direct=1 -iodepth 1 -thread -rw=randread -ioengine=psync -bs=16k -numjobs=10 -runtime=60 -group_reporting -name=mytest -size=2G (可直接用，向磁盘写一个2G文件，10线程，随机读1分钟，给出结果)
顺序读：fio -filename=/home/data-direct=1 -iodepth 1 -thread -rw=read -ioengine=psync -bs=16k -numjobs=2 -runtime=60 -group_reporting -name=mytest -size=1G
随机写：fio -filename=/home/data -direct=1 -iodepth 1 -thread -rw=randwrite -ioengine=psync -bs=16k -numjobs=2 -runtime=60 -group_reporting -name=mytest -size=1G
顺序写：fio -filename=/home/data -direct=1 -iodepth 1 -thread -rw=write -ioengine=psync -bs=16k -numjobs=2 -runtime=60 -group_reporting -name=mytest -size=1G
混合随机读写：fio -filename=/home/data -direct=1 -iodepth 1 -thread -rw=randrw -rwmixread=70 -ioengine=psync -bs=16k -numjobs=2 -runtime=60 -group_reporting -name=mytest -ioscheduler=noop -size=1G
```

### 网络性能
```
Iperf测试网络性能，需要安装：yum install iperf3 -y
服务端：iperf3 -s （或者 iperf3 -p <port> -s）
客户端：iperf3 -c <server-address>（或者 iperf3 -p <port> -c <server-address>）
```

### 系统各项性能跑分
```
源码包：
https://centos.pkgs.org/7/nux-dextop-x86_64/unixbench-5.1.3-1.el7.nux.x86_64.rpm.html
硬件平台通过   yum localinstall UnixBench-5.1.3-1.el7.aarch64.rpm安装：
其它两个系统需要编译：
wget http://soft.laozuo.org/scripts/UnixBench5.1.3.tgz
tar xf UnixBench5.1.3.tgz（tar xvzf unixbench-5.1.2.tar.gz）
cd UnixBench
make
执行 ./Run
※注意：如果出现错误-bash: ./Run: /usr/bin/perl: bad interpreter: No such file or directory。
输入yum groupinstall "Perl Support"即可。
 ```
 
 
### 比较权威的跑分工具
https://www.phoronix.com/scan.php?page=phoronix_news
 
https://github.com/phoronix-test-suite/phoronix-test-suite/releases

```
密码学测试
phoronix-test-suite benchmark cryptography
phoronix-test-suite benchmark botan
phoronix-test-suite benchmark scimark2
phoronix-test-suite benchmark openssl

系统内核性能
phoronix-test-suite benchmark kernel
phoronix-test-suite benchmark compress-gzip
phoronix-test-suite benchmark compress-7zip

网络测试
phoronix-test-suite benchmark netperf
phoronix-test-suite benchmark iperf
phoronix-test-suite benchmark network-loopback

系统启动时间
phoronix-test-suite benchmark systemd-boot-total


cpu
phoronix-test-suite benchmark smallpt
phoronix-test-suite benchmark npb
phoronix-test-suite benchmark crafty
phoronix-test-suite benchmark cachebench

中间件
phoronix-test-suite benchmark nginx
phoronix-test-suite benchmark java-scimark2
phoronix-test-suite benchmark pgbench
phoronix-test-suite benchmark go-benchmark

磁盘与文件系统
phoronix-test-suite benchmark tiobench
phoronix-test-suite benchmark fs-mark
phoronix-test-suite benchmark compilebench
phoronix-test-suite benchmark fio

内存性能
phoronix-test-suite benchmark ramspeed
phoronix-test-suite benchmark stream

深度学习
phoronix-test-suite benchmark caffe
```

```
pts/all
pts/benchmark (基准)
pts/java
pts/golang
pts/lapack (线性代数)
pts/linux
pts/system
pts/cpu
pts/memory
pts/disk
pts/multicore （多线程）
pts/network
pts/processor (CPU)
pts/docker
```






