# mihomo-rules

> ⚙️ Mihomo 规则集仓库
> 
## 📁 目录结构
```
mihomo   #可执行文件
rules/
   独立规则集/
      yaml     # 未编译的 YAML 规则文件
      mrs      # 转换后的 .mrs 规则文件
svg/     # 图标资源
```

## 🚀 使用说明

### 1. 编写规则文件
在 `rules/` 中创建一个规则集，例如：
```floder
Wechat/
Game/
claude/
...
```
进入规则集内,如:
cd Wechat
#### 域名规则
```yaml
payload:
  - "+.example.com"
  - "keyword:game"
```

#### IP 规则
```yaml
payload:
  - "43.160.156.23/32"
  - "119.29.29.98/32"
  - "106.8.179.54/32"
```

---

### 2. 转换为 `.mrs`
使用 Mihomo 工具：
```bash
mihomo convert-ruleset ipcidr yaml rules/Wechat/Wechat_ip.yaml rules/Wechat/Wechat_ip.mrs
mihomo convert-ruleset domain yaml rules/Wechat/Wechat_Domain.yaml rules/Wechat/Wechat_Domain.mrs
```
[了解更多](https://bk.zbbp.net/index.php/archives/156/)


---

### 3. 在主配置中引用
```yaml
  Wechat_域:
    <<: *Domain
    path: ./rules/Wechat_域.mrs
    url: "https://cdn.jsdelivr.net/gh/Magma-71453/mihomo-rules@main/mihomo/rules/Wechat/Wechat_Domain.mrs"    
  Wechat_IP:
    <<: *IPCIDR
    path: ./rules/Wechat_IP.mrs
    url: "https://cdn.jsdelivr.net/gh/Magma-71453/mihomo-rules@main/mihomo/rules/Wechat/Wechat_ip.mrs"
```

---

## 📖 规则类型说明
| 类型 | 描述 | 示例 |
|------|------|------|
| domain | 域名规则 | `+.example.com` / `keyword:foo` |
| ipcidr | IP 或网段 | `8.8.8.8/32` / `1.1.1.0/24` |

---

## 📜 License
个人自用规则集，允许参考与复用。

---

## 🌟 致谢
感谢 [mihomo](https://github.com/MetaCubeX/mihomo) 项目。
