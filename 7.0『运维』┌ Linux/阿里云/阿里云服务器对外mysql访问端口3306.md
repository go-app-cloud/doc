

# 阿里云服务器安全组对外3306端口

服务器--- 管理 --- 安全组 ---- 安全组列表  --- 配置规则  --- 添加安全组规则


```
网卡类型： 内网
规则方向： 入方向
授权策略： 允许
协议类型： MySQL(3306)
端口范围: 3306/3306
优先级： 1
授权类型： IPv4地址端访问
授权对象： 0.0.0.0/0
描述： 描述
```

