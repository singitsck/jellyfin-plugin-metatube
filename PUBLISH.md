# 发布到 GitHub 清单

我这边不能直接替你创建 GitHub 空仓库。按下面做完，把仓库 URL 发回来即可推送。

## 1. 在 GitHub 建空库

建议：

- Owner：`singitsck`
- 名称：`jellyfin-plugin-metatube`
- 公开（Public）
- **不要**勾选 README / LICENSE / .gitignore（本地已有）

## 2. 替换占位 URL

编辑根目录 `manifest.json`，把所有：

`https://github.com/singitsck/jellyfin-plugin-metatube/...`

改成真实用户名（例如 `singitsck`）。

同样检查 `README.md` 里安装示例中的 raw 地址。

## 3. 首次推送（示例）

```bash
cd jellyfin-plugin-metatube
git init
git add .
git commit -m "Initial: MetaTube JF12 build 2026.1019.1.0"
git branch -M main
git remote add origin git@github.com:singitsck/jellyfin-plugin-metatube.git
git push -u origin main
```

## 4. 发 Release

- Tag：`v2026.1019.1.0`
- 附件：`releases/Jellyfin.MetaTube@v2026.1019.1.0.zip`
- `manifest.json` 里的 `sourceUrl` 必须指向该 Release 附件的下载地址

## 5. 在 Jellyfin 添加仓库

Raw URL：

`https://raw.githubusercontent.com/singitsck/jellyfin-plugin-metatube/main/manifest.json`

## 本地暂存位置

本机（助手工作区）：`/workspace/jellyfin-plugin-metatube/`
