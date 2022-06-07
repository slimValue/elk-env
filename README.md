### elk环境部署

在Services中声明了四个服务：

- elasticsearch；
- logstash；
- kibana；
- filebeat；

#### 使用方式

```shell

cp .env.example .env
# 修改env配置
# ....

# 拷贝配置
cp filebeat/config/filebeat-example.yml filebeat/config/filebeat.yml
cp kibana/config/kibana-example.yml kibana/config/kibana.yml
cp logstash/pipline/logstash-example.yml logstash/pipline/logstash.yml

# 修改配置
# ....

# 在启动ES容器时，需要先创建好宿主机的映射目录
# 并且配置映射目录所属
sudo chown -R 1000:1000 ${DOCKER_MOUNT_DIR}/elasticsearch/data
sudo chown -R 1000:1000 ${DOCKER_MOUNT_DIR}/filebeat/data

# 启动
docker-compose up -d

# 关闭
docker-compose down
```

#### logstash

目录映射:
```
logstash/pipeline ---- /usr/share/logstash/pipeline
logstash/config   ---- /usr/share/logstash/config
```


```shell

chmod 777 -R ./logstash
chmod 777 -R ./logstash/data
chmod 777 -R ./logstash/logs

```