## 02-安装 JDK

```bash
roles/jdk/
├── files
│   └── jdk-8u251-linux-x64.tar.gz
├── tasks
│   └── main.yml
├── templates
│   └── jdk.sh.j2
└── vars
    └── main.yml
```

## 获取源码包

自行到 [Oracle 官网下载](https://www.oracle.com/technetwork/java/javase/archive-139210.html)   下载后将软件包放置到 roles/jdk/files/ 目录下。

## 需要修改的地方

```bash
$ cat roles/jdk/vars/main.yml
PKG_VERSION: 8u251  # JDK 安装包上的版本号，如 jdk-8u251-linux-x64.tar.gz
JDK_VERSION: 1.8.0_251 # 这个版本号是安装包解压以后的目录名字
JAVA_HOME: /usr/local/jdk # 指定了 JAVA_HOME 的位置
```

## ansible 主机清单参考

```bash
$ cat /etc/ansible/hosts
[news]
10.10.11.11

# 下面定义的 SOFTWARE_DIR 变量是存放安装包的位置，必须要有
[news:vars] 
# 存放安装包的位置,哪个磁盘分区大就放到哪
SOFTWARE_DIR=/home/fosafer
```

## 验证

```bash
$ ansible-playbook  02.jdk.yml
```
