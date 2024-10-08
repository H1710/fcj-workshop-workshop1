---
title: "Launch an Redis"
date: 2024-09-22
weight: 4
chapter: false
pre: "<b> 4. </b>"
---

## 4. Launch a Redis

1. Go to Elastic Cache console
   ![alt text](ElasticcacheConsole.png)
2. Launch Redis Cluster
   ![alt text](CreateRedis.png)
3. Setting networking for redis
   ![alt text](RedisNetworking.png)
4. Download and set up redis-cli

```bash
sudo yum install redis6 -y
```

5. Access Redis CLI

```bash
redis6-cli -h <Redis_Cluster_Endpoint> -p <Redis_Port> --tls
```

6. Check Redis CLI

```bash
ping
```
