# 00-系统初始化

```bash
roles/initsys/
├── files
│   └── base-rpm.tar.gz
├── handlers
│   └── main.yml
├── tasks
│   ├── base.yml
│   ├── hostname.yml
│   ├── main.yml
│   ├── security.yml
│   └── sysctl.yml
└── templates
    ├── 20-nproc.conf.j2
    ├── locale.conf.j2
    ├── login.sh.j2
    └── sysctl.conf.j2
```

## /etc/ansible/host 配置参考

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
$ ansible-playbook 00.initsys.yml
```







