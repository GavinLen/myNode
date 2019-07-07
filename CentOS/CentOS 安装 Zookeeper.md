# README

```shell
#!/bin/sh
echo "start zkServer..."
for i in 1 2 3
do
ssh mini$i "source /etc/profile;/root/apps/zookeeper-3.4.5/bin/zkServer.sh start"
done
```

