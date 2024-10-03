### 常用命令介绍

(1) ctrl c: 取消命令，并且换行

(2) ctrl u: 清空本行命令 ps windows下 为 esc

(3) tab键：可以补全命令和文件名，如果补全不了快速按两下tab键，可以显示备选选项

(4) ls: 列出当前目录下所有文件，蓝色的是文件夹，白色的是普通文件，绿色的是可执行文件

ls -l 展示详细信息、ls -lh 文件大小换算、ls -a 显示隐藏文件 

(5) pwd: 显示当前路径

(6) cd XXX: 进入XXX目录下

(7) cp XXX YYY: 将XXX文件复制成YYY，XXX和YYY可以是一个路径，比如../dir_c/a.txt，表示上层目录下的dir_c文件夹下的文件a.txt

(8) mkdir XXX: 创建目录XXX

(9) rm XXX: 删除普通文件;  rm XXX -r: 删除文件夹 全称：remove
	-f，--force：直接删除，不再询问
	-r，-R，--recursive：递归删除，即删除所有子目录和子目录下的文件
	-d，--dir，删除空目录
	rmdir 删除空的子目录

(10) mv XXX YYY: 将XXX文件移动到YYY，和cp命令一样，XXX和YYY可以是一个路径；重命名也是用这个命令

(11) touch XXX: 创建一个文件

(12) cat XXX: 展示文件XXX中的内容

(13) 复制文本
    windows/Linux下：Ctrl + insert

(14) 粘贴文本
    windows/Linux下：Shift + insert

(15) 创建用户
	useradd aaa // 创建用户名为 aaa 的用户
	useradd -g group1 aaa // 创建用户名为 aaa 的用户并归到 group1 组内

(16) 创建组
	groupadd group1 // 创建名为 group1 的组

(17) 切换用户
	su 用户名
	该命令可以实现任何身份的切换，包括从普通用户切换为 root 用户（su root）、从 root 用户切换为普通用户以及普通用户之间的切换。
	普通用户之间切换以及普通用户切换至 root 用户，都需要知晓对方的密码，只有正确输入密码，才能实现切换；从 root 用户切换至其他用户，无需知晓对方密码，直接可切换成功。

### linux 优点

1、提供了先进的网络支持，内置 TCP/IP 协议
2、真正意义上的多任务、多用户操作系统
3、开放源代码，用户可以自己对系统进行改造
4、支持数十种文件系统格式

### 权限

通过 ls –l 查看当前目录的详细属性
权限为 drwxrwxr-x，d 表示目录，同一位置如果为 - 则表示普通文件
rwxrwxr-x 表示三种角色的权限，每三位为一种角色，依次为 user，group，other 权限，如上则表示 user 的权限为 rwx，group 的权限为rwx，other 的权限为r-x

+ chmod(change mode) 控制用户对文件的权限的命令

  -R : 对目前目录下的所有文件与子目录进行相同的权限变更(即以递归的方式逐个变更)

  chmod  –R  g+rwx  peter // 授予组对 peter 目录拥有 rwx 权限

  chmod  –R  u=rx,g=rx,o=rx  peter // 授予用户、组、其他人对 peter 目录只有 rx 权限

  chmod  –R  777  peter // 授予用户、组、其他人对 peter 目录拥有 rwx 权限

### vim

![image-20221206171150672](D:\typora\typora-user-images\image-20221206171150672.png)

```
1、在一般模式：
yy // 复制当前行
5yy // 复制当前行向下的5行（包括当前行）
p // 粘贴
dd // 删除当前行
10dd // 删除当前行向下的5行（包括当前行）
u // 撤销
gg // 光标移动到首行
G // 光标移动到末行
20G // 光标移动到第20行

2、在一般模式下输入 / 进入查找模式:
/关键字 回车，再输入 n 查找下一个

3、在一般模式下输入 : 进入命令模式:
:set nu // 设置行号
:set nonu // 取消行号
```
### C / C++ 源文件

+ 步骤：预处理、编译、汇编、链接

```
gcc test.c -o test2 //编译为 test2.out 文件
g++ test.c // 编译 C++ 文件
./test2.out // 运行 test2.out 可执行文件，相当于 exe 文件
```

### 路径

cd .. 返回上层目录

cd 或 cd ~ 或 cd ~/，进入家目录， 即 /home/zouweiyi

cd /，进入根目录即 /

### 常见目录

| 目录  | 说明                                                         |
| ----- | ------------------------------------------------------------ |
| /bin  | 存放二进制可执行文件(ls,cat,mkdir等)，常用命令一般都在这里   |
| /etc  | 存放系统管理和配置文件                                       |
| /home | 存放所有用户文件的根目录，是用户主目录的基点，比如用户 user 的主目录就是 /home/user |

### 标准 I/O

+ 操作系统提供的功能
  1、系统调用

  + 进程控制
  + 进程间通信
  + 文件系统控制
  + 存储管理
  + 网络管理
  + 套接字控制
  + 用户管理

  2、用户程序编程接口

+ linux 遵循 POSIX 标准

+ 标准 I/O 遵循 ANSI 规范

+ 分类
  全缓冲、行缓冲、无缓冲

+ mode 取值

  | mode | 解释1          | 解释2          |
  | ---- | -------------- | -------------- |
  | r    | 只读           | 文件必须存在   |
  | r+   | 可读写         | 文件必须存在   |
  | w    | 只写           | 覆盖原有文件   |
  | w+   | 可读写         | 覆盖原有文件   |
  | a    | 附加打开只写   | 不覆盖原有文件 |
  | a+   | 附加打开可读写 | 不覆盖原有文件 |

### 文件I/O

+ VFS

  Virtual File System，虚拟文件系统，把各种具体的文件系统的公共部分抽取出来，形成一个抽象层。VFS 是应用程序与具体的文件系统之间的桥梁，处于系统内核空间
+ 文件分类
普通文件、目录文件、符号链接文件、管道文件、套接字文件、设备文件
+ 文件 IO 与 标准 I/O
  文件：低级磁盘 I/O，每次操作都会执行相关的系统调用
  标准：高级磁盘 I/O，在文件 I/O 基础上封装了缓冲机制
+ fcnt() 函数
  file control，用来操作文件描述符，对已打开的文件进行各种操作，能够管理文件锁，获取和设置文件相关标志位以及复制文件描述符
+ 文件锁
  1、建议性锁，要求每个相关程序在访问文件之前检查是否有锁存在，并尊重已有锁，由 lockf() 实现
  2、强制性锁，由内核执行的锁，当一个文件被上锁，进行写入操作时，阻止任何程序读写，由 fcntl() 实现

### 进程控制

+ 任务与进程
  一个任务包含一个或多个完成独立功能的进程

+ 进程与线程
  进程是并发执行的程序在执行过程中分配和管理资源的基本单位，是一个动态概念，每个进程都有自己的数据段、代码段和堆栈段。线程是进程的一个执行单元，是调度的基本单位，一个进程可以拥有多个线程。线程也被称为轻量级进程

+ 只有用户级线程的操作系统中，调度以进程为单位，由用户程序控制进程中的多个线程运行

+ 每个执行的程序都成为一个进程。每个进程都分配一个 ID 号（pid）

+ 进程特性：
  并发性、动态性、交互性、独立性

+ 进程类型：
  交互式、批处理、守护

+ 进程状态
  1、运行
  2、可中断的阻塞
  3、不可中断的阻塞
  4、暂停
  5、僵死
  6、消亡

+ fork() 函数
  用于从已存在的进程中创建一个新进程
  在子进程中返回 0 
  在父进程中返回 子进程的 PID

+ exit() 与 _exit() 的区别
  exit() 在终止当前进程之前检查该进程打开了哪些文件，并把文件缓冲区中的内容写回文件中
  _exit() 直接使进程停止运行

+ wait() 与 waitpid() 的区别
  wait() 使父进程阻塞，直到一个子进程结束或者该进程接到了一个指定的信号为止
  waitpid() 提供了非阻塞版本的 wait() 功能，并不一定等待第一个终止的子进程

+ 进程存在方式：
  前台：用户目前的屏幕上可以进行操作的进程
  后台：实际在操作，但屏幕上无法看到的进程，如 mysql、tomcat

+ 常见参数
  pid  process identity，进程号
  ppid  parent process identity，父进程号
  grep  Global Regular Expression Print，文本搜索
  %CPU  进程占用CPU的百分比
  %MEM  进程占用物理内存的百分比
  VSZ  Virtual Memory Size，进程占用的虚拟内存大小
  RSS  Resident Set Size，进程占用的物理内存大小STAT  进程状态
  STARTED  进程的启用时间
  TIME  进程使用CPU的时间

+ ps命令用来查看目前系统中执行的进程

  ```
  ps -a // 显示当前终端的所有进程信息
  ps -u // 以用户的格式显示进程信息
  ps -x // 显示后台进程运行的参数
  ps -aux // 组合使用
  ps -aux | grep xxx // 文本搜索
  ps -ef // 以全格式显示当前所有的进程
  ps -aux | grep bash // 查看终端进程
  ps -aux | grep sshd // 查看远程连接进程
  ```

+ kill命令用来终止进程

  ```
  kill [选项] 进程号
  kill -9 进程号 // 强制终止进程
  ```

### 进程通信

+ 分类

  1、传统：管道、信号

  2、System V：共享内存、消息队列、信号灯

  3、BSD：套接字

+ 管道

  将前一个命令的标准输出作为后一个命令的标准输入，称之为管道

  1、无名管道（匿名管道）

  ​	创建两个文件描述符，fd[0] 用于读管道，fd[1] 用于写管道

  ​	如果所有写进程都关闭了管道的写端时，read 返回 0，意味着文件的结束

  ​	只能以单工的方式通信

  ​	如果管道中无数据，则读进程将被挂起直到数据被写进管道

  2、有名管道

  创建命名管道除了使用 mkfifo 函数外，还可以使用 mknod 函数

  + 区别

    无名管道只能用于具有亲缘关系的进程的通信

    有名管道可以使互不相关的两个进程实现彼此的通信

+ 信号

  + 信号通信机制可用于异步通信
  + 信号处理函数：kill()、raise()、alarm()、signal()、sigaction()、pause()
  + 常用信号
    SIGINT：interrupt request，中断请求信号（可屏蔽），在输入 Ctrl + C 后发出
    SIGQUIT：在输入 Ctrl + \ 后发出
    SIGKILL：立即结束程序的运行，不能被阻塞、处理和忽略
    SIGSTOP：暂停一个进程，不能被阻塞、处理和忽略

+ 共享内存

  + 最为高效的通信方式
  
  + 适用于在进程间传输大量的数据
  
  + 使用共享内存无法解决多个进程同时读写的冲突
  
  + 指令
  
    ```
    ipcs -m // 查看已经创建的共享内存情况
    ipcrm -m 43 // 删除指定共享内存
    ```
  
  + shmget() 创建私有共享内存
  
    ```c
    int main() {
        system("ipcs -m");
        
        int shmid;
        shmid = shmget(IPC_PRIVATE, 128, 0666);
        if (shmid < 0) {
            printf("failed!");
            return -1;
        }
        printf("success, shmid = %d\n", shmid);
        system("ipcs -m");
        return 0;
    }
    ```
  
  + shmget() 用 key 来创建共享内存
  
    ```C
    int main() {
        system("ipcs -m");
    
        key_t key;
        key = ftok(".", 'a'); // 创建 key
        if (key < 0) {
        	printf("key ERRER!");
        	return -2;
        }
        printf("key = %x\n", key);
    
        int shmid;
        shmid = shmget(key, 128, IPC_CREAT | 0666); // 传入 key
        if (shmid < 0) {
            printf("failed!");
            return -1;
        }
        printf("success, shmid = %d\n", shmid);
        system("ipcs -m");
        return 0;
    }
    ```
  
  + shmat()
    把创建的共享内存映射到具体的进程空间中
  
  + shmdt()
    撤销映射
  
  + shmctl()
    传入 IPC_RMID 删除共享内存
  
+ 消息队列
  可以实现消息的随机查询，比 FIFO 具有更大的优势。这些消息存在于内核中
  
+ 信号灯（信号量）
  信号量可以用于实现多进程间的同步与互斥

  + semget(key, nsems, semflg)
    创建信号量或获得系统已存在的信号量，key 是信号量的键值，nsems 是创建信号量的个数，semflg 是信号量的权限位
  + semctl()
    初始化信号量
    传入 IPC_SETVAL 设置信号量的值
    传入 IPC_RMID 删除信号量
  + semop()
    进行信号量的 PV 操作

+ 套接字
套接字可用于不在同一台主机的两个进程通信

### 多线程

+ 线程运行在用户空间

+ 线程属性：

  分离属性、堆栈大小、调度策略、优先级

+ 生产者与消费者为何使用 3 个信号量：

  avail 和 full 用于解决生产者和消费者线程之间的同步问题，mutex 用于这两个线程之间的互斥问题
  avail 表示缓冲区中的空单元数，full 表示缓冲区中非空单元数，mutex 是互斥信号量
  
+ 信号量的互斥

  <img src="D:\typora\typora-user-images\image-20221207214652464.png" alt="image-20221207214652464" style="zoom:70%;" />

+ 信号量的同步

  <img src="D:\typora\typora-user-images\image-20221207214746332.png" alt="image-20221207214746332" style="zoom:70%;" />

### 网络

+ 端口号是 16bit 的地址码，端口号和 IP 地址构成一个插口（socket）
+ 一个完整的网络程序应该包含两个独立的程序，它们分别运行在客户端和服务器端
+ OSI 参考模型与 TCP/IP 参考模型
  <img src="D:\typora\typora-user-images\image-20221207151531846.png" alt="image-20221207151531846" style="zoom:60%;" />
+ 常见协议
  网络接口层：ARP、RARP
  网络层：ICMP、IP、IGMP
  传输层：TCP、UDP
+ 选择
  TCP：对数据可靠性要求高的应用，网络状态不是很好的情况
  UDP：对实时性要求高的应用
  相同条件下 UDP 发送数据的速度要比 TCP 快
  UDP 具有比 TCP 更好的网络性能，经常用于视频会议直播中
+ 套接字类型
  流式套接字、数据报套接字、原始套接字
+ TCP、UDP 流程

![image-20221207151815428](D:\typora\typora-user-images\image-20221207151815428.png)

 <center>图 TCP流程</center>



![image-20221207151845826](D:\typora\typora-user-images\image-20221207151845826.png)

<center>图 UDP流程</center>

  
