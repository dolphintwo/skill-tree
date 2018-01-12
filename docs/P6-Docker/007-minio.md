# docker安装minio

## 安装
```bash
docker pull minio/minio
```
## 启动
```bash
docker run -d -p 8787:9000 --name minio \
  -v /mnt/minio/data:/data \
  -v /mnt/minio/config:/root/.minio \
  -e "MINIO_ACCESS_KEY=dolphintwo" \
  -e "MINIO_SECRET_KEY=abc960095049"  \
  minio/minio server /data
```

## 客户端配置
```
yum install -y epel-release
yum install -y s3cmd
```
`.s3cfg`

```
# Setup endpoint
host_base = 218.245.66.229:7480
host_bucket = 218.245.66.229:7480
bucket_location = us-east-1
use_https = False

# Setup access keys
access_key = M0X0Y98CIQGRFI6NSRLN
secret_key = qovih4AbuDPbmQUzo1svF2B85U0OqpzaE0mJu3zh

# Enable S3 v4 signature APIs
signature_v2 = False
```
操作
```
s3cmd mb s3://test
s3cmd ls
```


host_base = 218.245.66.229:7480
host_bucket = 218.245.66.229:7480
bucket_location = us-east-1
use_https = False

access_key = M0X0Y98CIQGRFI6NSRLN
secret_key = qovih4AbuDPbmQUzo1svF2B85U0OqpzaE0mJu3zh

signature_v2 = False