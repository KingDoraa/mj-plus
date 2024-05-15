## Docker部署教程

### 升级版本
⚠️ 注意: **不要删除docker容器**
1. 获取最新版本的app.jar
2. 替换到config目录下，注意jar文件名需为app.jar
3. 重启容器，不需要重新激活
    ```shell
    docker restart midjourney-proxy-plus
    ```
4. 若服务有问题，请查看docker日志
    ```shell
    docker logs -f -n 100 midjourney-proxy-plus
    ```

### 初次部署
1. /xxx/xxx/config目录下创建
    > 注意: /xxx/xxx是 服务器目录示例，需自行修改
   - `app.jar` 最新的jar包，下载并命名为app.jar
   - `application.yml` mj配置项，参考 https://github.com/litter-coder/midjourney-proxy-plus/blob/main/resources/application.yml
   - `banned-words.txt` 非必须，覆盖默认的敏感词文件，参考 https://github.com/litter-coder/midjourney-proxy-plus/blob/main/resources/banned-words.txt

2. 启动容器，映射config目录
    ```shell
    docker run -d --name midjourney-proxy-plus \
     -p 8080:8080 \
     -v /xxx/xxx/config:/home/spring/config \
     novicezk/plus-jdk17:latest
    ```
3. 若服务有问题，请查看docker日志
    ```shell
    docker logs -f -n 100 midjourney-proxy-plus
    ```

4. 访问 `http://ip:port` 查看管理页面，用户名默认是admin，密码默认是设置的接口密钥（未设置默认密码是admin）
5. 登录后按照指引激活服务