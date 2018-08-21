# jenkins-部署

## 配置环境

下载jenkins
<pre>
wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
mv jenkins.war /usr/local/src/
</pre>

运行jenkins
<pre>
nohup java -jar /usr/local/src/jenkins.war --ajp13Port=-1 --httpPort=8089 &
</pre>

安装jenkins的docker插件

![image](https://github.com/shenxinli/jenkins-/blob/master/jenkins-docker-plugin.png)

部署私有deoker仓库
<pre>
docker run -d -p 5000:5000 -v /opt/data/registry:/var/lib/registry  registry
</pre>

编辑docker启动参数
<pre>
vi /usr/lib/systemd/system/docker.service
</pre>
写入docker-register的ip和端口号,如下图：

![image](https://github.com/shenxinli/jenkins-/blob/master/modify-docker-service.png)

在jenkins中配置配置私有docker仓库,[系统管理]-[系统设置]下新增云

![image](https://github.com/shenxinli/jenkins-/blob/master/jenkins-docker-instance.png)

## 创建部署任务

![image](https://github.com/shenxinli/jenkins-/blob/master/new-jenkins-task.png)

### 配置任务属性
设置git远程库和访问账户

![image](https://github.com/shenxinli/jenkins-/blob/master/jenkins-task-properties.png)

配置构建属性
![image](https://github.com/shenxinli/jenkins-/blob/master/jenkins-task-build.png)

