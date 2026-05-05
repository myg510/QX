# QuantumultX 配置仓库

个人 QuantumultX 配置 + 自维护规则集合。基于 [@ddgksf2013 墨鱼配置 v2.0/V267](https://ddgksf2013.top/Profile/QuantumultX.conf) 在其上做了节点策略优化、银行直连、AI 服务全量分流等改造。

## 订阅地址

```
https://raw.githubusercontent.com/myg510/QX/main/QuantumultX.conf
```

QuantumultX → 设置 → 订阅 → 粘贴上方地址。

## 主要特性

- **节点策略**：在原有的 香港/台湾/日本/狮城/美国 之上新增 `NF解锁`、`IPLC优选`、`韩国节点` 三个智能策略组
- **银行直连**：内置 11 家中国银行域名规则（工商/农业/中国/建设/交通/招商/光大/广发/中信/邮储/平安），全部 force-policy=direct
- **AI 全量分流**：三层覆盖
  - `Ai.yaml`（@ddgksf2013）— 主流厂商
  - `AI Suite`（@dler-io）— Augment / Windsurf / Trae / Zed / Groq / OpenRouter / Sora / Apple Intelligence
  - `AI-Extra.list`（本仓库）— Suno / Udio / ElevenLabs / Runway / Pika / Luma / HuggingFace / Replicate / Cohere / Mistral / Stability / Civitai / Bolt.new / v0 / Lovable / Replit / Devin / DeepL / You.com / Phind / Manus 等冷门服务
- **番茄小说去广告**：使用 [@fmz200/wool_scripts](https://github.com/fmz200/wool_scripts) 活跃维护版本（含 host 屏蔽 + IP-CIDR 屏蔽 + URL 正则拦截）
- **广告净化**：墨鱼去开屏 + 微博去广告 + 网易云净化 + Cats-Team AdRules

## 仓库结构

```
.
├── QuantumultX.conf          主配置
├── rewrite/                  rewrite 规则备份（来自上游各作者）
│   ├── StartUpAds.conf
│   ├── WeiboAds.conf
│   ├── NeteaseAds.conf
│   ├── UnblockURLinWeChat.conf
│   └── FanQieNovel.snippet
└── filter/                   filter 规则备份
    ├── AI-Extra.list         ⭐ 本仓库自维护，被 conf 直接引用
    ├── AI-Suite.list         上游备份
    ├── Ai.yaml               上游备份
    ├── Banks/                11 家银行规则备份（来自 LM-Firefly）
    ├── AdRules.qx.conf
    ├── Apple.list / WeChat.list / Streaming.list / Proxy.list / ASN.China.list
    └── ...
```

> **注**：除 `AI-Extra.list` 外的所有规则，conf 都直接引用上游 raw URL（自动跟随上游更新）。`rewrite/`、`filter/` 中的副本仅作离线备份，不被 conf 引用。

## 自定义 AI-Extra

需要新增 AI 服务分流，编辑 [`filter/AI-Extra.list`](filter/AI-Extra.list)：

```
DOMAIN-SUFFIX,新服务域名.com
```

提交并推送，QuantumultX 长按风车 → 更新订阅资源即可生效（每周自动更新一次）。

## 致谢

| 来源 | 内容 |
|---|---|
| [@ddgksf2013](https://github.com/ddgksf2013) | 配置框架基础、广告净化规则、Ai.yaml |
| [@fmz200](https://github.com/fmz200/wool_scripts) | 番茄小说去广告 |
| [@dler-io](https://github.com/dler-io/Rules) | AI Suite 规则集 |
| [@LM-Firefly](https://github.com/LM-Firefly/Rules) | 银行域名规则 |
| [@Cats-Team](https://github.com/Cats-Team/AdRules) | 广告终结者 |
| [@blackmatrix7](https://github.com/blackmatrix7/ios_rule_script) | 微信 / 苹果 / 国际媒体规则 |
| [@KOP-XIAO](https://github.com/KOP-XIAO/QuantumultX) | resource-parser、流媒体解锁查询脚本 |
| [@ConnersHua](https://github.com/ConnersHua/RuleGo) | 全球加速规则 |
| [@VirgilClyne](https://github.com/VirgilClyne/GetSomeFries) | 国内 ASN 规则 |
| [@Koolson/Qure](https://github.com/Koolson/Qure)、[@Orz-3/mini](https://github.com/Orz-3/mini) | 图标资源 |

## License

仅供个人学习与自用参考。各上游规则版权归原作者所有，请遵守其许可协议。
