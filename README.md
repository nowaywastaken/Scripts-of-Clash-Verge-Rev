# Proxy-Rules

集中维护常用代理规则（分流、阻断、直连等），方便在 Clash / Surge / Quantumult X / AdGuard 等网络代理工具中直接订阅或导入使用。

> 说明：请根据仓库中实际的规则文件名与目录对下文的链接与示例进行替换与调整。

## 目录
- [简介](#简介)
- [支持的规则格式](#支持的规则格式)
- [快速开始](#快速开始)
- [使用示例](#使用示例)
- [更新与同步策略](#更新与同步策略)
- [贡献指南](#贡献指南)
- [常见问题](#常见问题)
- [许可协议](#许可协议)
- [维护者与联系方式](#维护者与联系方式)

## 简介
本仓库旨在集中、规范地维护常用的代理规则集合，便于：
- 快速部署到各类代理客户端；
- 在不同客户端格式之间进行转换；
- 社区协同维护、持续更新规则库以应对网络变化。

规则通常用于：
- 分流（按域名/IP/端口/关键词分配至不同出口或直连）；
- 广告与跟踪阻断；
- 常见服务/地区策略（直连、代理、拒绝）。

## 支持的规则格式
- Clash (YAML)
- Surge (conf)
- Quantumult X (rewrite, filter)
- AdGuard Home / AdGuard (filters)
- 以及通用 Hosts / ACL 列表

（实际仓库中有哪些格式请查看 `rules/` 或根目录下的文件）

## 快速开始

克隆仓库（适用于想查看或本地修改）：
```bash
git clone https://github.com/nowaywastaken/Proxy-Rules.git
```

直接在客户端中订阅（示例）：
- Clash（示例 URL — 请替换为仓库实际文件的 raw 地址）  
  `https://raw.githubusercontent.com/nowaywastaken/Proxy-Rules/main/clash.yaml`
- Surge / Quantumult X / AdGuard 同理，使用对应的 raw 文件地址导入订阅。

手动导入规则：
1. 在仓库中找到对应格式的规则文件（如：`rules/clash/*.yaml`、`rules/surge/*.conf`）。
2. 将文件复制到你的客户端订阅/配置目录，或通过客户端“导入”功能加载文件内容。

## 使用示例

Clash 配置片段（将仓库的规则文件作为 RuleProvider 或直接合并）：
```yaml
rule-providers:
  my-rules:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/nowaywastaken/Proxy-Rules/main/clash.yaml"
    path: ./rules/my-rules.yaml
```

Surge 导入：
- 在 Surge 的远程配置中填入仓库中的 `surge.conf` raw 链接，或将内容粘贴进配置文件。

Quantumult X：
- 导入 filter/rewrite 列表的 raw 链接，或粘贴规则文本到对应模块。

## 更新与同步策略
- 所有改动请通过 Pull Request 提交；
- 对规则进行修改时，请在 PR 中注明修改缘由、测试方法与适用客户端；
- 重大规则调整应在合并前经过 Issues 或讨论确认，以避免影响下游使用者。

## 贡献指南
欢迎贡献！请按以下步骤：
1. Fork 仓库并在本地创建分支：`git checkout -b feat/your-change`
2. 修改或新增规则文件，确保遵守已有格式与注释规范。
3. 提交并发起 Pull Request，说明改动内容与测试方法。
4. 若规则来源于第三方，请注明来源与许可信息。

建议在提交时：
- 提供变更说明（CHANGELOG）或在 PR 描述中列明影响范围；
- 对于新增规则，包含简短注释以便后续维护。

## 常见问题
- Q：如何确认某条规则是否生效？  
  A：建议在本地客户端开启日志/调试功能，或使用 curl/traceroute 等工具验证流量走向。

- Q：可以把规则合并到我的配置中吗？  
  A：可直接订阅 raw 链接或将内容复制到你的配置中。若用于商业目的，请遵守仓库许可并注明来源。

## 许可协议
本仓库的内容采用 [请在此处填写许可协议，例如 MIT/Apache-2.0/CC BY-SA]。若规则包含来自第三方的条目，请遵循原始来源的许可证要求并在变更中标注来源。

## 维护者与联系方式
维护者：nowaywastaken  
如果你希望报告问题、提交建议或请求新功能，请通过 GitHub Issues 提交。

欢迎 star ⭐ 和 fork，感谢你的贡献与使用！
