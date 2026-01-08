# rule

规则集和配置文件仓库，用于 Clash （openclash/clash for android）/ quanx等代理工具。

## 文件说明

### 配置文件

- **sinbreak.ini** - OpenClash 配置文件模板（用于 OpenWrt 上的 OpenClash）
- **sinbreak-clash-android.ini** - Clash for Android 配置文件模板（用于 Android 手机上的 Clash for Android）
- **sinbreak-quanx.ini** - QuanX 专用配置文件模板（用于 Mac/iOS 上的 Quantumult X，移除 GEOSITE 规则）

### 规则集文件

- **Direct.list** - 直连规则列表
- **ProxyLite.list** - 轻量代理规则列表
- **AI.list** - AI 服务规则列表
- **BanProgram.list** - 应用净化规则列表

## 使用 subconverter 转换订阅

### 本地 subconverter 地址

```text
http://xxx.xxx.xxx.xxx:25500/sub
```

### 转换链接格式

```text
http://xxx.xxx.xxx.xxx:25500/sub?target={目标格式}&url={订阅链接}&config={配置文件}
```

### 参数说明

- **target**: 目标格式

  - `clash` - Clash 格式
  - `quanx` - Quantumult X 格式
  - 其他格式请参考 [subconverter 文档](https://github.com/tindy2013/subconverter)
- **url**: 订阅链接（需要 URL 编码）
- **config**: 配置文件路径或 URL（需要 URL 编码）

### 示例链接

#### OpenClash (Clash 格式)

```text
http://xxx.xxx.xxx.xxx:25500/sub?target=clash&url=[订阅地址，需要URL转码]&config=https%3A%2F%2Fraw.githubusercontent.com%2Fjs882829%2Frule%2Fmaster%2Fsinbreak.ini&emoji=true&udp=true
```

#### Clash for Android 格式

```text
http://xxx.xxx.xxx.xxx:25500/sub?target=clash&url=[订阅地址，需要URL转码]&config=https%3A%2F%2Fraw.githubusercontent.com%2Fjs882829%2Frule%2Fmaster%2Fsinbreak-clash-android.ini&emoji=true&udp=true
```

#### QuanX 格式

```text
http://xxx.xxx.xxx.xxx:25500/sub?target=quanx&url=[订阅地址，需要URL转码]&config=https%3A%2F%2Fraw.githubusercontent.com%2Fjs882829%2Frule%2Fmaster%2Fsinbreak-quanx.ini&emoji=true&udp=true
```

### 本地配置文件路径

如果配置文件放在本地 subconverter 的工作目录下：

#### OpenClash

```text
http://xxx.xxx.xxx.xxx:25500/sub?target=clash&url=[订阅地址，需要URL转码]&config=sinbreak.ini&emoji=true&udp=true
```

## 功能特性

配置文件支持以下功能：

- ✅ 自动测速（使用 gstatic.com/generate_204 进行节点测速）
- ✅ 应用分流（支持 AI、YouTube、Netflix、TikTok、GitHub、Google、Telegram 等）
- ✅ 增强中国 IP 段（使用 GEOSITE/GEOIP 规则）
- ✅ 增强国外 GFW 列表
- ✅ 节点过滤（自动清洗说明性、广告性节点）
- ✅ 节点清洗（自动过滤流量、套餐、到期、防失联等说明性节点）
- ✅ DNS 防泄露（95% 常用网站已做到防泄露）
- ✅ GEOSITE/GEOIP 规则支持（内联规则，提高匹配速度）
  - 注意：QuanX 不支持 GEOSITE，请使用 `sinbreak-quanx.ini`
- ✅ 冷门节点组（排除五大区后的其他节点）

## 策略组说明

配置文件包含以下策略组：

### 主要策略组

- **🚀 节点选择** - 主节点选择策略组（包含所有节点类型）
- **🎯 全球直连** - 直连策略（国内网站直连）
- **🐟 漏网之鱼** - 默认策略（未匹配规则的流量）

### 自动选择策略组

- **♻️ 自动选择** - 自动选择最快节点（排除游戏节点）
- **♻️ 自动选择香港** - 自动选择最快香港节点
- **♻️ 自动选择美国** - 自动选择最快美国节点
- **♻️ 自动选择日本** - 自动选择最快日本节点
- **♻️ 自动选择新加坡** - 自动选择最快新加坡节点
- **♻️ 自动选择游戏** - 自动选择游戏节点
- **♻️ YouTube自动选择香港** - YouTube 专用香港节点自动选择

### 地区节点筛选

- **🇭🇰 香港节点** - 香港节点筛选
- **🇯🇵 日本节点** - 日本节点筛选
- **🇸🇬 新加坡节点** - 新加坡节点筛选
- **🇺🇲 美国节点** - 美国节点筛选
- **🧊 冷门节点** - 排除五大区（HK/JP/TW/US/SG）后的其他节点
- **🌐 其他地区** - 其他地区节点筛选

### 高级策略组

- **🔯 故障转移** - 按地区故障转移（香港、日本、新加坡、美国）
- **🔮 负载均衡** - 负载均衡策略组（美国、香港）
- **🐸 手动切换** - 手动选择节点（显示所有节点）

### 应用专用策略组

- **🤖 AI** - AI 服务策略组（OpenAI、Bard、Claude 等）
- **📹 YouTube** - YouTube 策略组
- **🎥 Netflix** - Netflix 策略组
- **🎵 TikTok** - TikTok 策略组
- **👨🏿‍💻 GitHub** - GitHub 策略组
- **🍀 Google** - Google 服务策略组
- **🪟 Microsoft** - Microsoft 服务策略组
- **🍎 Apple** - Apple 服务策略组
- **📲 Telegram** - Telegram 策略组
- **🎮 游戏平台** - 游戏平台策略组（Steam、Epic、Origin 等）
- **💧 Copilot** - Copilot 策略组
- **🐬 OneDrive** - OneDrive 策略组
- **📢 FCM** - Google FCM 策略组
- **♻️ Speedtest** - 测速工具策略组
- **🎞️ 国内媒体** - 国内媒体策略组
- **🌍 国外媒体** - 国外媒体策略组

## 规则集说明

配置文件使用以下规则集，采用混合规则源（外部列表 + GEOSITE/GEOIP 内联规则）：

### 直连规则

- **🎯 全球直连** - 中国域名和 IP 直连规则
  - **局域网IP段直连**（防止DNS解析）
    - 192.168.0.0/16（私有网络）
    - 10.0.0.0/8（私有网络）
    - 172.16.0.0/12（私有网络）
    - 127.0.0.0/8（本地回环）
    - 169.254.0.0/16（链路本地）
    - 使用 `no-resolve` 标志防止DNS解析，避免局域网IP被解析为代理IP（如198.18.x.x）
  - 私网直连（GEOSITE/GEOIP private）
  - 国内直连（GEOSITE/GEOIP cn）
  - 自定义直连列表
  - 局域网规则（LocalAreaNetwork.list）
  - Steam 中国区规则
  - 下载类规则

### 代理规则

- **🚀 节点选择** - 需要代理的域名规则
  - 自定义代理列表
  - GFW 列表
  - 地理位置非中国规则（GEOSITE geolocation-!cn）

### 应用规则

- **🤖 AI** - AI 服务规则
  - OpenAI、Bard、Claude 等（外部列表）
  - OpenAI GEOSITE 规则
  - AI 类别规则（category-ai-!cn）

- **📹 YouTube** - YouTube 规则
  - 外部列表 + GEOSITE youtube

- **🎥 Netflix** - Netflix 规则
  - 外部列表 + GEOSITE/GEOIP netflix

- **🎵 TikTok** - TikTok 规则
  - 外部列表 + GEOSITE/GEOIP tiktok

- **👨🏿‍💻 GitHub** - GitHub 规则
  - 外部列表 + GEOSITE/GEOIP github

- **🍀 Google** - Google 服务规则
  - 外部列表 + GEOSITE/GEOIP google

- **🪟 Microsoft** - Microsoft 服务规则
  - 外部列表 + GEOSITE/GEOIP microsoft

- **🍎 Apple** - Apple 服务规则
  - 外部列表 + GEOSITE apple

- **📲 Telegram** - Telegram 规则
  - 外部列表 + GEOSITE/GEOIP telegram

- **🎮 游戏平台** - 游戏平台规则
  - Steam、Epic、Origin、Sony、Nintendo

- **💧 Copilot** - Copilot 规则（Bing）

- **🐬 OneDrive** - OneDrive 规则

- **📢 FCM** - Google FCM 规则

- **♻️ Speedtest** - 测速工具规则

- **🎞️ 国内媒体** - 国内媒体规则

- **🌍 国外媒体** - 国外媒体规则

### 拦截规则

- **🍃 应用净化** - 应用净化规则（广告拦截）
- **🛡️ 隐私防护** - 隐私保护规则

### 规则优先级

规则按以下优先级匹配（自上而下）：

1. **局域网IP段直连**（Direct.list中的IP-CIDR规则，带no-resolve标志）
2. 私网直连（GEOSITE/GEOIP private）
3. 国内直连（GEOSITE/GEOIP cn）
4. 自定义规则列表
5. 应用分流规则
6. 地理位置规则
7. 漏网之鱼（FINAL）

**注意**：局域网IP段规则必须在最前面，确保在DNS解析之前就匹配到，避免被fake-ip处理。

## 配置文件说明

### QuanX 专用配置

**sinbreak-quanx.ini** 是专为 Quantumult X 设计的配置文件，主要区别：

- ❌ **移除所有 GEOSITE 规则**：QuanX 不支持 GEOSITE 内联规则
- ✅ **保留 GEOIP 规则**：QuanX 支持 GEOIP 规则
- ✅ **保留所有外部规则列表**：使用外部规则列表文件
- ✅ **功能保持一致**：策略组和其他功能与 Clash 版本相同

**使用建议**：

- Clash/OpenClash 用户：使用 `sinbreak.ini` 或 `sinbreak-clash-android.ini`
- QuanX 用户：必须使用 `sinbreak-quanx.ini`

## 节点管理

### 节点清洗

配置文件自动过滤以下类型的节点名称：

- 流量、套餐、到期、剩余、重置
- 官网、网站、最新网址、防失联、失联
- 公告、通知、TG、Telegram、电报、群、频道
- 说明、使用说明、QQ群、客服、工单、订阅
- Expire、Traffic、Reset、Remaining、Official、Website

### 节点分组

- **地区节点**：香港、日本、新加坡、美国
- **冷门节点**：排除五大区（HK/JP/TW/US/SG）后的其他节点
- **游戏节点**：专门用于游戏的节点
- **Large 节点**：大流量节点（用于故障转移和自动选择）

## 局域网IP和DNS配置说明

### 问题说明

在某些情况下，OpenClash可能会对局域网IP地址（如192.168.x.x）进行DNS解析，导致返回代理IP（如198.18.9.45）。`198.18.0.0/15` 是RFC 2544定义的基准测试IP段，通常被代理工具用作fake-ip范围。

### 解决方案

配置文件已内置以下保护机制：

1. **Direct.list中的局域网IP段规则**：
   - 在 `Direct.list` 文件开头添加了明确的局域网IP段规则
   - 使用 `no-resolve` 标志防止DNS解析
   - 规则顺序优先，确保在DNS解析前匹配

2. **配置文件中的私网规则**：
   - `[]GEOSITE,private` - 匹配私有域名
   - `[]GEOIP,private,no-resolve` - 匹配私有IP，不进行DNS解析

### OpenClash DNS配置建议

如果问题仍然存在，请检查OpenClash的DNS配置：

1. **DNS设置**：
   - 确保"使用本地DNS服务"已启用
   - 检查"Fake-IP"设置，确保局域网IP不被fake-ip处理
   - 在"DNS设置"的"自定义上游DNS服务器"中，确保局域网IP段不被解析

2. **DNS服务器配置**：
   - 如果DNS服务器（如192.168.50.253）本身配置了fake-ip，需要修改DNS服务器配置
   - 确保DNS服务器不会将局域网IP解析为代理IP

3. **验证方法**：
   ```bash
   # 测试局域网IP是否被正确解析
   dig 192.168.2.70
   # 应该返回 NXDOMAIN 或正确的IP，而不是 198.18.x.x
   
   # 检查DNS配置
   scutil --dns
   ```

### 注意事项

- `no-resolve` 标志非常重要，它告诉Clash不要对IP地址进行DNS解析
- 规则顺序很重要，局域网IP规则必须在所有其他规则之前
- 如果使用自定义DNS服务器，确保DNS服务器不会对局域网IP进行fake-ip处理
- 重新生成配置后，需要重启OpenClash服务使配置生效
