# docker-for-hexo
一个轻量级、hexo程序的docker镜像。

### 快速开始

1. 拉取镜像
```
docker pull leebroncc/hexo
```
2. 创建一个server容器并运行
```
docker run -p 4000:4000 --name hexo-server -d \
-v {本地博客路径}/source:/hexo/source \
-v {本地博客路径}/themes:/hexo/themes \
-v {本地博客路径}/_config.yml:/hexo/_config.yml \
-e USER_NAME="{github用户名}" \
-e USER_EMAIL="{github邮箱}" \
leebroncc/hexo s
```
`{本地博客路径}`为你的宿主机的hexo容器共享目录，这个目录是绝对路径

3. 访问`http://ip:4000`即可访问博客

### 部署

部署的前提是:

* 已经拉取了镜像
* _config.yml已经配置正确
* 宿主机需要安装git

```
docker run -p 4000:4000 --name hexo-server -d \
-v {本地ssh目录}/.ssh:/root/.ssh \
-v {本地博客路径}/source:/hexo/source \
-v {本地博客路径}/themes:/hexo/themes \
-v {本地博客路径}/_config.yml:/hexo/_config.yml \
-e USER_NAME="{github用户名}" \
-e USER_EMAIL="{github邮箱}" \
leebroncc/hexo s
```

即可部署成功。

### 如何构建本镜像

1. 下载源码

```
git clone https://github.com/leonGravel/docker-for-hexo.git
```

2. 构建镜像

```
cd docker-for-hexo
docker bulid -t hexo .
```

