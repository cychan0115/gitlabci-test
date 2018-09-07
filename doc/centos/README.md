# ci_cd_test

#### 项目介绍
	安装Centos 
	版本 7 
	ISO http://mirrors.aliyun.com/centos/7/isos/x86_64/CentOS-7-x86_64-Everything-1804.iso

#### 优化系统
	1 使用国内YUM源
		mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
		wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
		yum makecache
		yum -y update
	2 内核优化
		ulimit –n 265535
		/etc/security/limits.conf
		fs.file-max = 265535 
		/etc/sysctl.conf
		net.ipv4.ip_conntrack_max=265535

#### 安装教程

	1 安装DOCKER
	2 安装DOCKER-COMPOSE
	3 安装DOCKER-RESITEY(todo)


#### 使用说明

1. xxxx
2. xxxx
3. xxxx

#### 参与贡献

	Cychan


#### 资料
	https://www.linuxidc.com/Linux/2015-05/118084.htm