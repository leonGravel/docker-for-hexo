# Dexo
## 记录一下自己用部署踩的坑
1. 在dockerfile所在文件夹执行，创建hexo所需的环境镜像
```
docker build -t hexo .
```
2. 创建一个容器并运行
```
 docker run -it -d -p 4000:4000 -v /usr/local/dokerFile/Gexo/blog:/hexo/ --name hexo hexo
 ```
`/usr/local/dokerFile/Gexo/blog`为你的hexo容器共享目录
3. 进入容器
```
docker attach hexo
```
4. 接下来的操作，就和hexo的初始化一样了
什么`hexo g`,`hexo s`，不再赘述。
# TODO
* 镜像文件打包
* 更加详细的文档说明
* 想起来再写
