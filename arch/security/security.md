应用安全
---------------
![image](https://cloud.githubusercontent.com/assets/4953205/8473265/c4b93664-20da-11e5-9b50-904561f49002.png)

- 1、除了对外的服务器（149）需要 public IP 外，其他任何服务器（150、151、153）应该应该只有 private IP
- 2、149服务器 开启 80（HTTP）、2208（修改ssh默认22）端口 ，nginx haproxy
- 3、private cloud（内网） 150、151、152 （elasticsearch 集群、game server）