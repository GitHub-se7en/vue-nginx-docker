## vue项目部署到阿里云服务器上，使用nginx作为反向代理访问HTML页面，使用docker容器化技术
#### 坑
坑爹的玩意，docker只认识自己生成的文件，我在notepad++里面自己编的conf根本不认识，而且坑爹的docker里面的文件粘贴不出来，只能使用命令复制文件出来，什么玩意
#### 第一步
把build之后的文件放到服务器上下面这个路径的文件夹里面，里面有一个dist文件夹，先删除，然后把本地的文件夹拖进去
```
/projectoa/view/
```
#### 第二步使用下面的命令启动项目就可以了
```
docker run -p 3006:80 -d --name vue-test -v /projectoa/view/nginx/conf.d:/etc/nginx/conf.d -v /projectoa/view/nginx/nginx.conf:/etc/nginx/nginx.conf -v /projectoa/view/dist:/usr/share/nginx/html nginx
```
解释一下需要改动的地方，3006是项目的端口，vue-test是容器的名字，也就是你这个项目现在跑在哪个容器里面
