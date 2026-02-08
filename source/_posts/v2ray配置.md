---
title: 创建 v2ray 配置
date: 2026-01-28 13:40:19
---

### 1. 创建服务器

centOS7 系统

### 2. 登录root账户

使用root账户和系统密码登录

### 3. 安装宝塔面板


```
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```

### 4. 登录宝塔面板

登录面板进行以下操作

### 5. 安装v2ray

```
bash <(curl -s -L https://git.io/v2ray.sh)
```

### 6. 放行端口

面板左侧，打开左侧的[安全]，放行对应的端口


## 通过这6个步骤，成功创建v2ray配置