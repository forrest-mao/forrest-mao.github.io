---
layout: post
title: 七牛云存储客户端上传回调失败
---

客户端收到七牛的`response`的`status code`为`579`时，即为上传成功但回调失败。下面有几种典型的情况：

1. 业务服务器地址不可达，即`callbackurl`非公网可访地址，解决方案是将`callbackurl`换成公网可访的地址；

2. 业务服务器拒绝七牛的回调请求，这样的一般是业务服务器将来自七牛的回调给过滤掉了，解决方案是配置允许七牛的回调UA的访问。
   七牛回调UA：http://kb.qiniu.com/user-agent ；

3. 业务服务器返回给七牛的body不是合法的Json串，一般错误信息是`{"error":"unexcepted response"}`：
    * 通过抓包，获取七牛返回给客户端的body，通过<http://jsonlint.com>验证是否回调的body为合法的json串；
    * 检查返回结果是否为`UTF-8`编码且带了`BOM`文件头，通过去掉`BOM`文件头可以解决该问题。