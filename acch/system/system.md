系统层架构图
---------------
![image](https://cloud.githubusercontent.com/assets/4953205/8428888/1cb3ece2-1f55-11e5-8e2c-4004bd711965.png)

- 1、Nginx Web Server的使用,预留负载均衡（配置一台upstream）、反向代理（这里80端口代理9200）、通过Nginx Web Server和Jetty Web Server 动静分离（静态文件、图片、下载通过nginx，其他请求通过jetty）