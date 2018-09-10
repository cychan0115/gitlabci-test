# Nexus

#### 项目介绍
	安装 Nexus
	版本 latest
	source https://hub.docker.com/r/sonatype/nexus/
#### 优化系统

#### 安装教程
	version: '2'
    services:
       nexus:
         image: sonatype/nexus3
         restart: always
         ports:
           - 8381:8081
         volumes:
           - "/etc/localtime:/etc/localtime"
           - "./nexus-data/:/nexus-data"
         environment:
           - INSTALL4J_ADD_VM_PARAMS=-Xms1200m -Xmx1200m -XX:MaxDirectMemorySize=2g -Djava.util.prefs.userRoot=/nexus-data

#### 使用说明
   

#### 参与贡献

	Cychan


#### 资料
