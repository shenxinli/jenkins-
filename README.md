# jenkins-部署

下载jenkins
<pre>
wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
mv jenkins.war /usr/local/src/
</pre>

运行jenkins
<pre>
nohup java -jar /usr/local/src/jenkins.war --ajp13Port=-1 --httpPort=8089 &
</pre>

部署私有deoker仓库
<pre>
docker run -d -p 5000:5000 -v /opt/data/registry:/var/lib/registry  registry
</pre>

编辑docker启动参数
<pre>
vi /usr/lib/systemd/system/docker.service

</pre>