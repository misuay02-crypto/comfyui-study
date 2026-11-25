# comfyui-study

面向初学者的中文 ComfyUI 离线学习桌面应用。提供课程、进度、笔记、资料库、AI 方向与跨电脑备份。

## Windows x64 下载

| 版本 | 下载 | SHA-256 |
| --- | --- | --- |
| 1.1.0 预览版 | [新版安装包](https://github.com/misuay02-crypto/comfyui-study/releases/download/v1.1.0-preview.1/comfyui-study-Setup-v1.1.0-x64.exe) | `bed06640749db14792762187cbd06dc7135fc3049102ff0f3dd66d0f096d112b` |
| 1.0.0 稳定版 | [稳定版安装包](https://github.com/misuay02-crypto/comfyui-study/releases/download/v1.0.0/comfyui-study-Setup-v1.0.0-x64.exe) | `5F41C1B3F04B6A73F763AAEF64F946867F6F9100790BFB27909382C1A6CED671` |
| 1.0.0 模型路径测试版 | [旧测试版安装包](https://github.com/misuay02-crypto/comfyui-study/releases/download/v1.0.0-v2-model-paths/comfyui-study-Setup-v1.0.0-x64.exe) | `1BFD020432CC4B436646F07189FEB550D4E8A3B151E74136004BE6EADB5DAF6C` |

安装包均未进行 Authenticode 签名。核对你所选版本的校验值。

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\comfyui-study-Setup-v1.1.0-x64.exe'
```

## 1.1.0 新增

- 侧栏「用户管理」支持管理员搜索、添加、改名、重置和删除普通用户。首次管理员登录须修改初始密码。普通用户在「我的账号」修改自己的密码，重置密码或删除账号后旧会话失效。
- 「安装与资源管理」增加模型下载预检。检查公开 HTTPS 地址、文件大小、目标和同名冲突，记录待核对的许可证与 SHA-256。预检只生成计划。
- 「软件更新」可检查正式版本，并在桌面版 Codex 中打开带 V2.0 交接路径的待发送草稿。继续开发需要完整本地源码工作区，也可保存项目交接 Markdown。
- 改进浅色和深色界面及窄窗口下的操作布局。

## 安装和学习数据

1. 下载 Windows x64 安装包，启动安装向导后选择适合的安装目录。首次启动时选择独立的学习数据目录。
2. 1.1.0 的部署者应先登录初始化管理员并完成改密，再交付给其他人。学习数据以本地目录为单位。同一数据目录的普通用户保留原学习功能，删除账号保留学习记录。
3. 跨电脑学习可导出完整 `.aistudy` 备份，另一台电脑预览并导入，后续传送增量包。学习备份不携带账号和会话。
4. 1.1.0 会升级数据目录中的 SQLite 结构。升级前请保留原目录的离线副本。已经迁移的目录继续用 1.1.0 或兼容的更高版本打开。

应用提供 12 节课程、可搜索的 20 个 AI 方向和 5 套入门方案。学习进度、文字笔记、资料和图片标注在本机离线保存。

## 技术栈

| 层级 | 技术 |
| --- | --- |
| 桌面 | Electron 45.5、内置 Node.js 24 |
| 界面 | React 19.3、Vite 8.3、CSS |
| 存储与账号 | SQLite、FTS5、加盐 scrypt、本地会话 |
| 模型路径与备份 | YAML 2.9、`.aistudy`、SHA-256 |
| 构建与验证 | electron-builder 26、NSIS、Windows x64、Node.js 测试运行器、Playwright |

## 验收范围

66 项自动化测试分别在 Node.js 和 Electron 内置 Node 通过。Windows 11 x64 的开发版和打包版通过桌面回归。ComfyUI 启动配置和同名文件优先级以官方 v0.46.0 源码进行四组隔离验证。完整 ComfyUI 和 Desktop 实例、真实模型加载、Windows 10 双机及本预览版的安装升级卸载流程仍待验收。
