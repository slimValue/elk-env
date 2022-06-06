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


### 设置nginx

`cat /etc/kibana/kibana.yml`

```yaml
# Default Kibana configuration for docker target
server.name: kibana
server.host: "0"
server.basePath: "/elk"
elasticsearch.hosts: [ "http://elasticsearch:9200" ]
xpack.monitoring.ui.container.elasticsearch.enabled: true
i18n.locale: "zh-CN"
```

`# systemctl restart kibana`
```
# netstat -nltp |grep 5601
tcp        0      0 127.0.0.1:5601          0.0.0.0:*               LISTEN      72068/node
```


### logstash

目录映射:
```
logstash/pipeline ---- /usr/share/logstash/pipeline
logstash/conf ---- /usr/share/logstash/config

```


```shell

chmod 777 -R ./logstash
chmod 777 -R ./logstash/data
chmod 777 -R ./logstash/logs

```