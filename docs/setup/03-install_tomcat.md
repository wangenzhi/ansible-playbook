# 03-安装Tomcat服务

```bash
roles/tomcat/
├── files
│   └── apache-tomcat-9.0.37.tar.gz
├── tasks
│   └── main.yml
├── templates
│   └── tomcat.service.j2
└── vars
    └── main.yml
```

## 获取源码包

下载 Tomcat 程序包 [Tomcat 官网下载](https://tomcat.apache.org/)   下载后将软件包放置到 roles/tomcat/files/ 目录下。

## 需要修改的地方

```bash
$ cat roles/tomcat/vars/main.yml
PKG_VERSION: 9.0.37 # Tomcat 安装包的版本号，如 apache-tomcat-9.0.37.tar.gz
TOMCAT_HOME: /usr/local/tomcat # Tomcat 安装完成后会软链接到这个位置
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
$ cat 03.tomcat.yml
- hosts: news
  remote_user: root
  roles:
  - jdk # 如果之前单独安装了 jdk 这里就不需要了
  - tomcat
  
$ ansible-playbook 03.tomcat.yml
```
