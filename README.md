# Clash / Mihomo Custom Rules

这是一个公共 Clash / Mihomo 自定义规则仓库，用于维护可公开共享的域名规则。

本仓库只保存规则，不保存任何节点信息。洛杉矶节点和大阪节点可以同时引用这套规则。

## 文件说明

- `rules/custom-proxy.yaml`：普通国外网站、打不开的网站。
- `rules/custom-ai.yaml`：普通 AI 平台补充规则。
- `rules/custom-direct.yaml`：国内软件、国内服务、远程控制类直连补充规则。
- `rules/custom-reject.yaml`：自定义拦截规则。
- `examples/provider-example.yaml`：主 YAML 中引用本仓库规则的示例。

## 本地配置边界

主 YAML 中的节点、DNS、`proxy-groups`、核心 AI 三处同步规则仍然保留在本地，不放进本仓库。

核心 AI 域名仍建议在本地主 YAML 的以下三处同步维护：

- `rules`
- `dns.nameserver-policy`
- `dns.fallback-filter`

## 维护方式

- 普通新增国外网站：加到 `rules/custom-proxy.yaml`。
- 普通 AI 平台：加到 `rules/custom-ai.yaml`。
- 国内软件 / 国内服务：加到 `rules/custom-direct.yaml`。
- 自定义拦截：加到 `rules/custom-reject.yaml`。

Clash / Mihomo 会根据 `rule-providers` 中的 `interval` 自动拉取规则。示例配置使用 `3600` 秒。

## 安全要求

不要把以下内容提交到本仓库：

- 完整 Clash / Mihomo YAML
- VLESS 链接
- VPS IP
- UUID
- Reality `public-key`
- Reality `short-id`
- 订阅链接
- 面板端口、SSH 端口
- 个人本地路径

如需生成本地修改版 YAML，请只输出到 `private/` 或 `local-output/`，这两个目录已被 `.gitignore` 忽略。
