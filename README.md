# Dexo
## 记录一下自己用docker部署hexo踩的坑
1. 在dockerfile所在文件夹执行，创建hexo所需的环境镜像
```
docker build -t hexo .
```
2. 创建一个容器并运行
```
 docker run -it -d -p 4000:4000 -v /usr/local/dokerFile/Dexo/blog:/hexo/ --name hexo hexo
 ```
`/usr/local/dokerFile/Dexo/blog`为你的宿主机的hexo容器共享目录，这个目录是绝对路径

3. 进入容器
```
docker attach hexo
```
如果此命令不行，建议使用id匹配

4. 接下来的操作，就和hexo的初始化一样了

在容器内执行hexo的部署。什么`hexo g`,`hexo s`，不再赘述。（`如果是linux主机，还需要开放一下端口，我这里设置的4000`） 

这里有一个问题是，如果你创建容器的时候，指定的端口是4000，那么你在容器内部署hexo的时候，不能够用
`hexo s -p  xxx`指定别的端口，我并没有反复验证这个地方。待确认~
# TODO
* 镜像文件打包
* 更加详细的文档说明
* 想起来再写
