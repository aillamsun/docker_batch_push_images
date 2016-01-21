# docker_batch_push_images
使用shell 批量上传docker images到注册服务器中，默认是本地注册服务器 127.0.0.1:5000


### 前提准备
    *查看docker images list
```shell
docker images
```
    *下载sh
```shell
$ git https://github.com/sungang1120/docker_batch_push_images.git;
```
    *赋权限
```shell
$ chmod a+x push_images.sh
```   

### 使用说明
```shell
    ./push_images.sh ubuntu:latest centos:centos7
    The registry server is 127.0.0.1
    Uploading ubuntu:latest...
    The push refers to a repository [127.0.0.1:5000/ubuntu] (len: 1)
    Sending image list
    Pushing repository 127.0.0.1:5000/ubuntu (1 tags)
    Image 511136ea3c5a already pushed, skipping
    Image bfb8b5a2ad34 already pushed, skipping
    Image c1f3bdbd8355 already pushed, skipping
    Image 897578f527ae already pushed, skipping
    Image 9387bcc9826e already pushed, skipping
    Image 809ed259f845 already pushed, skipping
    Image 96864a7d2df3 already pushed, skipping
    Pushing tag for rev [96864a7d2df3] on {http://127.0.0.1:5000/v1/repositories/ubuntu/tags/latest}
    Untagged: 127.0.0.1:5000/ubuntu:latest
    Done
    Uploading centos:centos7...
    The push refers to a repository [127.0.0.1:5000/centos] (len: 1)
    Sending image list
    Pushing repository 127.0.0.1:5000/centos (1 tags)
    Image 511136ea3c5a already pushed, skipping
    34e94e67e63a: Image successfully pushed
    70214e5d0a90: Image successfully pushed
    Pushing tag for rev [70214e5d0a90] on {http://127.0.0.1:5000/v1/repositories/centos/tags/centos7}
    Untagged: 127.0.0.1:5000/centos:centos7
    Done
```

### 查看仓库信息
```java
    curl http://127.0.0.1:5000/v1/search
    
    {"num_results": 7, "query": "", "results": [{"description": "", "name": "library/miaxis_j2ee"}, {"description": "", "name": "library/tomcat"}, {"description": "", "name": "library/ubuntu"}, {"description": "", "name": "library/ubuntu_office"}, {"description": "", "name": "library/desktop_ubu"}, {"description": "", "name": "dockerfile/ubuntu"}, {"description": "", "name": "library/test"}]}
```

* 这里可以看到 ``{"description": "", "name": "library/test"}``，表明镜像已经被成功上传了。
