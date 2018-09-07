# gitlab-runner

#### 项目介绍
	安装 gitlab
	版本 runner latest
	source https://hub.docker.com/r/gitlab/gitlab-runner/
#### 优化系统

#### 安装教程
	这里为发加快进度用了DOCKER来安装
    sudo docker pull gitlab/gitlab-runner:latest



    sudo docker run -d --name gitlab-runner-1 --restart always \
      -v /srv/gitlab-runner/config:/etc/gitlab-runner \
      -v /var/run/docker.sock:/var/run/docker.sock \
      gitlab/gitlab-runner:latest
    ###这里有一个要注意的地方以上是错的，以下才是正确
    sudo docker run -d --name gitlab-runner-2 --restart always \
      -v /srv/gitlab-runner/config:/etc/gitlab-runner \
      -v /var/run/docker.sock:/var/run/docker.sock \
      --add-host gitlabci.com:192.168.2.63 \
      gitlab/gitlab-runner:latest
    
    sudo docker exec -it gitlab-runner-1 gitlab-ci-multi-runner register
    
    sudo docker exec -it gitlab-runner-2 gitlab-ci-multi-runner register
    #这里填入TOKEN和URL，如果要注册多个runner就运行多次

#### 使用说明
    按本次实例的token来生成runner


#### 参与贡献

	Cychan


#### 资料
	https://www.linuxidc.com/Linux/2015-05/118084.htm
    https://blog.csdn.net/aixiaoyang168/article/details/72168834
    http://192.168.2.63:10080/admin/runners
    Install GitLab Runner
        Specify the following URL during the Runner setup: http://192.168.2.63:10080/ 
        Use the following registration token during setup: _1c7cnrEyB5wfwsfL1gS 
        Start the Runner!