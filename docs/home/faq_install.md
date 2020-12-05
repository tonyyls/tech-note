# 安装过程出错

这里记录安装各种软件/package过程中频繁出现的问题。

## 错误一

> Failed to connect to raw.githubusercontent.com port 443: Connection refused
在安装github上的资源的时候，经常会报这种错误，`Connection refused`。此时是无法 `ping` 通该地址的，需要配置Host来做个代理。

方案：
1. 进入 `https://www.ipaddress.com/` 查看 `raw.githubusercontent.com` 对应的IP地址。
2. 进入 `etc/hosts`（mac , linux） 修改映射，添加如下：

```
199.232.28.133 raw.githubusercontent.com
```
3. 退出终端重启生效


