
外网服务器IP
--------------------------
>ssh root@120.52.145.147

nginx
--------------------------
>nginx转发规则配置文件

>/var/opt/gitlab/nginx/conf/gitlab-http.conf

gitlab
--------------------------
>http://120.52.145.147

>配置修改 /var/opt/gitlab/gitlab-rails

sonar
--------------------------
>http://120.52.145.147/sonar

>后端服务端口：9000

rap
--------------------------
>http://120.52.145.147:8080

>部署路径：/www/apache-tomcat-7.0.59/webapps/ROOT

>快速学习教程： http://thx.github.io/RAP/study.html#

>Mockjs学习：http://mockjs.com/

jenkies
--------------------------
>http://120.52.145.147:8080/jenkins

>部署路径：/www/apache-tomcat-7.0.59/webapps/jenkins

本地文件共享服务器 
--------------------------
> \\\\192.168.1.122\share

>或者

> \\\\MASH-D0011\share

Maven 镜像配置
--------------------------
>修改setting.xml 的`<mirrors>` 加入以下配置
```javascript
   <mirror>
      <id>nexus</id>
      <mirrorOf>*</mirrorOf>
      <name>Human Readable Name for this Mirror.</name>
      <url>http://192.168.1.122:8181/nexus/content/groups/public/</url>
   </mirror>
```