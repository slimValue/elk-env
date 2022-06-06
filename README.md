### elk环境部署

在Services中声明了四个服务：

- elasticsearch；
- logstash；
- kibana；
- filebeat；


在启动ES容器时，需要先创建好宿主机的映射目录；
并且配置映射目录所属，例如：
```shell
 sudo chown -R 1000:1000 ${DOCKER_MOUNT_DIR}/elasticsearch/data
```
