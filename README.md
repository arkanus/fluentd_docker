# Docker + Fluent + ElasticSearch + Kibana

Simple POC on using [fluentd](http://www.fluentd.org/) to achieve results
similar to the [ELK stack](https://www.elastic.co/webinars/introduction-elk-stack).

## Requirements

To run this you only need docker installed on your system, I used dokcer machine
on OSX. Also you must have `docker-compose`.

## How to use

First start the servers

```bash
docker-compose up -d
```

Optionally watch the logs (this will take over this terminal)

```bash
docker-compose logs
```

Then launch a docker container, directing it's logs to fluentd

```bash
docker run --rm --name=lolg --log-driver=fluentd --log-opt fluentd-address=192.168.99.100:24224 elasticsearch
```

In this case we launched another instance of elasticsearch (yes, it's a crappy
example, I know)

Enter-the kibana front on `http://<local or docker machine ip>:5601` configure
and enjoy the view.
