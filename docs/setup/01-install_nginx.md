## 01-安装 Nginx 服务

```bash
roles/nginx/
├── defaults
│   └── main.yml # 默认变量，定义了 Nginx 版本和 Nginx 默认安装位置
├── files
│   └── nginx.tar.gz # nginx 安装包
├── handlers
│   └── main.yml
├── tasks
│   └── main.yml
└── templates
    ├── nginx.conf.j2 # nginx 主配置文件
    └── nginx.sh.j2 # nginx 环境变量
```

## 获取源码包

自行到 Nginx 官网下载 nginx-x.xx.x.tar.gz 的软件包放置到 `roles/nginx/files/` 目录下。

## 需要修改的地方

```bash
$ cat roles/nginx/defaults/main.yml
---
# Nginx Version
NGINX_VERSION: 1.18.0 # Nginx 版本号
NGINX_DIR: /usr/local/nginx # 编译安装时 Nginx 的安装位置
```
## ansible 主机清单参考

```bash
$ cat /etc/ansible/hosts
[news]
10.10.11.11

[news:vars]
# 存放安装包的位置,哪个磁盘分区大就放到哪
SOFTWARE_DIR=/home/fosafer
```

## 验证

```bash
ansible-playbook --check 01-nginx.yml
```

验证成功后去掉 `--check` 执行任务

```bash
ansible-playbook 01-nginx.yml
```

验证服务是否运行

```bash
ps -ef | grep "nginx"
```


