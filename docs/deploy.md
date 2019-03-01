# 如何部署

此篇幅讲述如何安装部署这个网站cms， 分成三部分服务器， 数据库和如何部署运行

-----



## 服务器

1. 安装Ubuntu 16.04.4 LTS, 参考https://blog.csdn.net/flyyufenfei/article/details/79187656

2. 安装 nodejs 环境， 在命令行里

   ```
   sudo apt-get update
   sudo apt-get install nodejs
   sudo apt-get install npm
   ```

3. 检查安装成功, 在命令行里输入，

   ``` 
   npm -v
   nodejs -v
   ```



## 数据库

安装mongodb 数据库， 这里给出的官方安装方法，还有很多不同安装办法可百度。监控软件可以考虑studio 3T

### 方法一 （官网）

1. 第一步, 命令行运行

1. ``` 
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
   ```

2. 第二步

   ```
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
   ```

3. 第三步

   ``` sudo apt-get update
   sudo apt-get update
   ```

4. 第四步

   ```
   sudo apt-get install -y mongodb-org
   ```

```
//开始mongodb
sudo service mongod start 或者直接在mongodb根目录运行./mongod

//关闭
sudo service mongod stop

//重启
sudo service mongod restart
```

数据库监控软件可以考虑studio 3T, 链接如下

https://studio3t.com/download/



## 部署

1. 安装 yarn

   ``` 
   sudo apt-get update && sudo apt-get install yarn
   ```

2. 进入到项目根目录， 安装依赖包

   ```
   yarn install
   ```

3. 运行部署

   ````
   yarn run prod
   ````

4. 监控运行， 可以支持远程在线监控，更多详情可以参考http://pm2.keymetrics.io/， 此部分还会未来完善。。。

   ```
   //监控运行状态
   sudo pm2 list
   //删除该部署
   pm2 delete [id]
   //重启
   pm2 restart [id]
   //查看运行日志
   sudo pm2 logs 
   //重启anyproxy
   sudo pm2 restart [id]
   //监控内存占用
   sudo pm2 monit
   ```
