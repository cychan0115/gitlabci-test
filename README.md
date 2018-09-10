# ci_cd_test

#### 项目介绍
说明：基于centos搭建docker +gitlab （CI/CD）持续集成环境
步骤：
 （1）安装gitlab，使用CI/CD功能
  要求： 安装gitlab  runner，编写(gitlab-ci.yml) ，在代码提交，更新时触发ci/cd
  
（2）安装docker 
 要求：安装docker-compose，编写（docker-compose.yml ），使用compose编排命令定义和运行复杂应用程序,使用dockerfile构建符合实际需求的镜像文件。

#### 软件架构



#### 安装教程
    教程放在对应的目录下面
    
    
#### 结果图
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/11.png)
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/22.png)
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/33.jpg)
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/44.png)
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/55.png)
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/66.png)
![image](https://raw.githubusercontent.com/cychan0115/gitlabci-test/master/77.png)

#### 小记

    把项目S2CAT，放到GITLAB上，搭建配置CI gitlab-ci.yml

    之后用docker-compose 来部署项目

    要求：
        使用工具 Maven jdk tomcat nexus habor

    software
    description
    Note
    gitlab-ce
    csv

    gitlab-runner
    ci

    docker
    deploy

    docker-compose
    compose	

    Maven
    compile

    tomcat jdk
    java

    Nexus	
    private server

    Habor
    docker registry UI


    这里把东西分三块

    1 版本中心
        gitlab
    2 编译中心
        gitlab runner
        maven/jdk/tomcat/Nexus
    4 部署生产
        Harbor
        docker-compose

    场景设计:
        开发人员完成程序把代码合并到test分支并PUSH

    CI/CD操作：
        收到test分支的提交后，执行测试和部署，发布到测试服务器。等待QA工作。


    小结：
        其实这里实现复杂，不过路线是很清晰的，用gitlab代码管理，用CI脚本来做激活事件，通过DIND的方法，生成一个docker让这个docker 去BUILD一个实例镜像，之后推送到harbor上，之后用调用测试服务器，部署/升级。

    坑有几大个

    1 harbor网上的教程太多错了，要结合官网自己看
    2 harbor要用http 一定要配置好参数，还有每一个docker的服务主要都要配置，配置时要注意格式问题。
    3 gitlab上的dind要细看，有几个关键参数。
    4 docker-compse  还有很多TODO的，不过为了加快面试进度，就不修改了。
    5 这里有一个难点，如果在docker里跑的dind，里配置harbor的非https配置。
    6 在DOCKER里的DOCKER操作，要非常注意对象，不然很容易走弯路


    CI/CD实现
    1 编写gitlab-ci.yml ci过程由runner来运行

    docker-compose 设计




    images:docker:latest

    variables:
     ssh:”host”
    stages:






    Runner

    这里主要注意一下dns，其它没有太多要注意的地方


    tomcat


    jar




    Habor
    https://codeload.github.com/goharbor/harbor/tar.gz/v1.6.0-rc3


    要配置非https访问方法



    这里有一点要注意网上很多教程都是不对的有问题的，自己看了一个官方和文档和说明解决了问题
    docker tag mytomcat reg.cy.com/mytomcat/image
    docker push reg.cy.com/mytomcat/image


    Nexus

    https://hub.docker.com/r/sonatype/nexus/
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



