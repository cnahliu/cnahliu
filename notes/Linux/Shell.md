##代码片段

1. 统计日志中iOS设备访问总数

> 打印日志中含有openid=的日志行

```bash
grep 'iPhone OS 8' ./*.log |grep 'openid'|awk  '{print $6}' | awk 'BEGIN{FS="openid="} {print $2}'| awk 'BEGIN{FS="&"} $1 !="" {print $1}' >iOS8.txt
```
> 去重后计数

```bash
sort -n iOS8.txt |uniq |wc -l
```
