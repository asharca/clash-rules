# Clash Rules

个人 Clash 规则集，用于自定义代理规则。

## 文件结构

```
clash-rules/
├── README.md
└── list/
    ├── claude.list       # Claude / Anthropic 相关域名
    └── development.list  # 开发工具相关域名
```

## 使用方法

1. 获取 Raw 链接（替换 `你的用户名`）：
   - `https://raw.githubusercontent.com/你的用户名/clash-rules/main/list/claude.list`
   - `https://raw.githubusercontent.com/你的用户名/clash-rules/main/list/development.list`

2. 在 Clash 配置中引用：

```yaml
rule-providers:
  Claude:
    type: http
    behavior: classical
    url: "https://gh-proxy.com/raw.githubusercontent.com/你的用户名/clash-rules/main/list/claude.list"
    path: ./rule_provider/claude.list
    interval: 86400

  Development:
    type: http
    behavior: classical
    url: "https://gh-proxy.com/raw.githubusercontent.com/你的用户名/clash-rules/main/list/development.list"
    path: ./rule_provider/development.list
    interval: 86400

rules:
  - RULE-SET,Claude,Claude
  - RULE-SET,Development,Development
```

## 维护方法

1. 直接编辑 GitHub 上的 `.list` 文件并提交
2. Clash 会根据 `interval` 自动更新规则
3. 或手动在 Clash 中点击 **Update All**

## 推荐代理

为防止 GitHub Raw 被墙，建议通过以下加速服务访问：

- `https://gh-proxy.com/`
- `https://raw.fgit.ml/`
- `https://raw.iqiq.io/`
