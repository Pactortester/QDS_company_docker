# QDS_company_docker
linux + docker +python


1.	首先安装docker
Centos  yum install docker
其他 apt/apt-get install docker
2.	搜索镜像源(image)
安装完docker之后, service start docker,
搜索docker源 : docker search 需要的镜像(centos)
3.	拉镜像源
Docker pull 镜像源名称
系统默认 centos:latest v1.0
Docker pull 源:版本号
4.	实例化一个image
Docker run –v linux本地目录(/usr/abc):docker镜像目录(/abc/def) –p 6666:6666(多个) –dti docker源:版本号(docker image的ID) bash(bin/bash)

docker run -v /python_worker/:/home -dti centos:latest bash

5.	查看实例化的容器(container)
Docker ps –a
6.	进入实例化的容器
docker exec -it 2cf(docker 容器的ID 或者容器名字都行) bash

安装无界面chrome
https://blog.csdn.net/weixin_40476348/article/details/85992293

centos镜像下安装python
1.	安装依赖源gcc : yum install gcc
2.	下载linux的python包
https://www.cnblogs.com/freeweb/p/5181764.html
安装报错
https://www.cnblogs.com/sixiong/p/5711091.html



关于docker容器container

1.	用docker run 创建一个容器
2.	Docker start 容器名字/容器ID
3.	Docker exec –it 容器名字/ID bash
4.	结束docker stop 容器名/ID
5.	删除容器 docker rm –f 容器名/ID
6.	删除镜像 docker rmi 镜像名/ID

容器创建完成, 提交  docker commit 容器名/ID 自己起名字:版本号
容器保存本地镜像  docker save 镜像名/ID –o 本地目录/xxx.tar
加载本地已有的镜像  docker load –i 本地已存的docker tar包


Linux的chrome无头浏览器运行需要添加设置
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')


解决权大师上传图片的问题
	后端获取的是前端传过来的form表单, 而点击手动上传被添加了JS事件默认打开windows/mac/linux的窗口, 这里只需要找到form表单里对应的input框, 改变它的value即可自动模拟上传图片.
 
在Python的selenium下只需要执行JS

document.getElementsByName("colorBrandPic")[0].value = "/home/123.png"

即可完成上传, 相当于用JS给它赋值
 


Linux的定时任务
自带crontab

添加定时任务 : crontab –e
	* * * * * python3 /home/QDS_Test/run….py
