部署环境
-------------

####  1、环境配置
- 1、git version 1.9.5 (Apple Git-50.3)（本地需要）
- 2、Apache Maven 3.2.5（本地需要）
- 3、jdk 1.7 以上 (Java version: 1.7.0_75)
- 4、[jetty下载](http://download.eclipse.org/jetty/stable-8/dist/jetty-distribution-8.1.17.v20150415.zip) ,解压 upzip jetty-distribution-8.1.17.v20150415.zip

####  2、下载项目源码
- 1、[game-server源码](https://github.com/pengqiuyuan/game-server.git) 或者svn上下载源码

####  3、修改host、port
- 1、/game-server/src/main/resources/application.properties 

```
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://127.0.0.1:3306/game_server?useUnicode=true&characterEncoding=utf-8
jdbc.username=root
jdbc.password=

imagepath=/usr/local/share/www
imgUrl=http://127.0.0.1

#execlpath=/Users/apple/share/www/execl
excelpath=/home/dev/share/www/excel
excelUrl=http://10.0.10.251/excel

#billing
list_url=http://10.0.10.105:40000/api/gameserver/v1/gift/index
save_url=http://10.0.10.105:40000/api/gameserver/v1/gift/add
del_url=http://10.0.10.105:40000/api/gameserver/v1/gift/delete
export_url=http://10.0.10.105:40000/api/gameserver/v1/gift/export
review_url=http://10.0.10.105:40000/api/gameserver/v1/gift/review
search_url=http://10.0.10.105:40000/api/gameserver/v1/gift/search
searchgift_url=http://10.0.10.105:40000/api/gameserver/v1/gift/searchgift
```
- 2、/game-server/src/main/webapp/manage/count/config.js(查看代码说明)

```
//测试使用
//elasticsearch: "http://"+window.location.hostname+":9200",
	 
//线上使用 nginx 80 port 代理9200 
elasticsearch: "http://"+window.location.hostname+"/port",
```
- 3、/game-server/src/main/webapp/manage/count/vendor/elasticsearch.angular.js(查看代码说明)

```
//测试使用
//elasticsearch: "http://"+window.location.hostname+":9200",
    	 
//线上使用 nginx 80 port 代理9200 
elasticsearch: "http://"+window.location.hostname+"/port",

```


####  4、编译、打包war
- 1、进入项目根目录，pom.xml所在目录
- 2、执行编译 mvn compile
- 3、编译成功后，打包 mvn clean install -Dmaven.test.skip=true
- 4、打包成功后 game-server/target/game-server.war 目录下会生成game-server.war文件，这个就是我们需要部署的项目war包

####  5、上传war包到指定服务器
- 1、解压jetty，修改web容器名字为game-server
    - upzip jetty-distribution-8.1.17.v20150415.zip
    - mv jetty-distribution-8.1.17.v20150415 game-server


- 2、如：（game-server.war在game-server/target 目录下）
  - scp ./game-server/target/game-server.war root@10.0.29.249:/home/dev/game-server/webapps/ 
  

- 3、如：启动jetty，注意启动jetty之前，需要确保elasticsearch服务已经启动
  - game-server 目录下执行 bin/jetty.sh restart 
  - cd logs 查看日志确保服务正常启动 tail －f **.log




  