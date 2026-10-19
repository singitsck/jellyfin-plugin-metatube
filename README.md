# Jellyfin Plugin MetaTube（Jellyfin 12 社区构建）

> **非官方构建。** 基于 [metatube-community/jellyfin-plugin-metatube](https://github.com/metatube-community/jellyfin-plugin-metatube)（MIT），面向 **Jellyfin 12.x**（`targetAbi: 12.0.0.0`）。  
> 官方插件目前仍面向 Jellyfin 10.11；上游 JF12 相关 PR 合并后，请优先改用官方版。

中文说明如下；上游英文/日文原文见 [`docs/README.upstream.md`](docs/README.upstream.md)、[`docs/README.ja.upstream.md`](docs/README.ja.upstream.md)。

## 为什么需要这个仓库？

Jellyfin 12 使用 .NET 10，旧版 MetaTube（ABI 10.x）无法加载。本仓库提供已在 **Jellyfin 12.2.0** 上冒烟通过的插件包，方便自己备份，也方便他人通过插件目录安装。

## 当前发布

| 项 | 值 |
|----|----|
| 版本 | `2026.1019.1.0` |
| targetAbi | `12.0.0.0` |
| 测试 | Jellyfin 12.2.0（加载成功） |
| 包 | [`releases/Jellyfin.MetaTube@v2026.1019.1.0.zip`](releases/Jellyfin.MetaTube@v2026.1019.1.0.zip) |
| MD5 | `f9175ff00e0f1accb372a27baa4459f7` |

## 安装方式

### A. 插件目录（推荐）

1. 仪表盘 → 插件 → 目录 → 齿轮 → **添加仓库**
2. 仓库 URL 使用本仓库根目录的 `manifest.json` 的 raw 地址，例如：  
   `https://raw.githubusercontent.com/<你的用户名>/jellyfin-plugin-metatube/main/manifest.json`
3. 在目录中安装 **MetaTube**（应显示 ABI 12）→ 重启 Jellyfin

> 仓库建好并把 `manifest.json` 里的 `sourceUrl` / `imageUrl` 换成真实地址后，上面的 URL 才能用。见 [`PUBLISH.md`](PUBLISH.md)。

### B. 手动安装

1. 下载 Release 里的 `Jellyfin.MetaTube@v….zip`
2. 解压到 Jellyfin 的 `plugins/MetaTube/`（目录内应有 `MetaTube.dll`）
3. 重启 Jellyfin，确认日志出现 `Loaded plugin: MetaTube 2026.1019.1.0`

## 依赖

需要自建或可用的 [MetaTube Server](https://github.com/metatube-community/metatube-server)；在插件设置里填写 Server URL。本仓库**只包含 Jellyfin 插件**，不含 Server。

## 与官方的关系

- GUID 与官方 MetaTube 相同（`01cc53ec-c415-4108-bbd4-a684a9801a32`），用于同一插件身份，**不要与官方 10.x 包混装**。
- 许可证：MIT（见 [LICENSE](LICENSE)），版权归属 MetaTube Community。
- 上游 PR / 讨论请关注官方仓库；本仓库仅作 JF12 过渡发布。

## 本地构建

需要 .NET 10 SDK。

```bash
dotnet build Jellyfin.Plugin.MetaTube/Jellyfin.Plugin.MetaTube.csproj -c Release
```

Release 会生成 `Jellyfin.MetaTube@v{Version}.zip`（Version 按 UTC 时间生成）。

## 免责声明

成人向元数据插件；请遵守当地法律与上游项目约定。本构建不保证与未来 Jellyfin 小版本完全兼容。
