# comfyui-study

面向初学者的中文 ComfyUI 离线学习桌面应用，提供课程、学习进度、笔记、资料库和跨电脑备份。V2.0 测试版增加了 AI 方向库、ComfyUI 实例登记和自定义模型路径检查。

## 下载与安装

| 版本 | Windows x64 安装包 | 大小 |
| --- | --- | --- |
| 稳定版 `v1.0.0` | [下载稳定版](https://github.com/misuay02-crypto/comfyui-study/releases/download/v1.0.0/comfyui-study-Setup-v1.0.0-x64.exe) | 116.6 MiB |
| V2.0 模型路径测试版 `v1.0.0-v2-model-paths` | [下载测试版](https://github.com/misuay02-crypto/comfyui-study/releases/download/v1.0.0-v2-model-paths/comfyui-study-Setup-v1.0.0-x64.exe) | 116.7 MiB |

两个安装包同名，均未签名。请按所选版本核对 SHA-256。

| 版本 | SHA-256 |
| --- | --- |
| 稳定版 | `5F41C1B3F04B6A73F763AAEF64F946867F6F9100790BFB27909382C1A6CED671` |
| V2.0 测试版 | `1BFD020432CC4B436646F07189FEB550D4E8A3B151E74136004BE6EADB5DAF6C` |

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\comfyui-study-Setup-v1.0.0-x64.exe'
```

1. 下载 `.exe` 并运行安装向导。可选择自定义安装目录。
2. 首次启动时选择有写入权限的独立个人数据目录，例如 `D:\ComfyUIStudyData`。
3. 在学习首页打开课程，或从上次的位置继续。内置课程、笔记、资料管理和备份可离线使用，无需注册账号或另装 Node.js。

## 功能

- 稳定版提供 12 节离线课程，共约 308 分钟，涵盖生成模型、本地运行基础、ComfyUI 入门、工作流接线、扩散与采样参数。课程配有分层解释、术语、练习、课内自测和教学工作流示意。
- 保存阅读位置和已读标记，记录课程活跃学习时长。支持文字笔记、中文全文检索和资料原件导入。
- 支持完整或增量 `.aistudy` 备份、导入预览、冲突处理和附件恢复。可在设置中迁移或切换本机数据目录。
- V2.0 测试版提供 20 个可查询的 AI 方向及 5 套入门方案，支持登记本机 ComfyUI 实例和检查 `extra_model_paths.yaml`。

### 在测试版检查模型路径

在「安装与资源管理」打开已登记的 ComfyUI 实例，点击「检查自定义模型路径」。报告显示解析后的位置、分类搜索顺序、缺失目录、重复路径及共享候选。

检查范围限于实例根目录的 YAML 文件和本机目录元数据。搜索顺序按 ComfyUI v0.46.0 的单文件规则推算，网络路径和已识别的链接会被跳过。实际启动参数、Desktop 附加配置、目录权限和模型可加载性仍需在真实实例中核对。 [ComfyUI v0.46.0 加载规则](https://github.com/Comfy-Org/ComfyUI/blob/v0.46.0/utils/extra_config.py#L4-L33)

## 在两台电脑间续学

1. 在第一台电脑打开「备份与迁移」，导出完整 `.aistudy` 备份。
2. 用微信文件传输助手或其他可信方式发送备份。第二台电脑在应用中打开文件，预览后确认导入。
3. 后续可导出增量。若提示缺少基线，先按顺序导入完整包和缺少的增量。两边修改同一条记录时，可保留本地版本、采用导入版本或保留两份。

备份文件上限为 64 MiB，未加密。模型路径检查报告只在当前窗口显示。

## 技术栈

| 层级 | 技术 |
| --- | --- |
| Windows 桌面 | Electron 45.5.0，内置 Node.js 24.22.3 |
| 用户界面 | React 19.3.1、React DOM、Vite 8.3.8、CSS |
| 本地数据 | SQLite 3.54.1、`node:sqlite`、FTS5 中文全文搜索 |
| 备份 | `.aistudy` 格式、SHA-256 校验、增量游标和稳定记录标识 |
| 模型路径检查 | `yaml` 2.9.1，V2.0 测试版 |
| 安装打包 | electron-builder 26.18.0、NSIS、Windows x64 |
| 测试 | Node.js 测试运行器、Playwright |

## 验证范围

稳定版的 18 项核心测试通过。V2.0 测试版的 51 项自动化测试在 Node.js 和 Electron 内置 Node 中均通过。Windows 11 上的开发版和打包版通过桌面验证，路径检查使用两套合成 ComfyUI 目录。双向备份测试使用同一电脑上的两套数据目录。真实 ComfyUI、双机迁移、Windows 10，以及测试版的安装、升级和卸载流程仍待验证。

第 5–12 阶段课程、真实 ComfyUI 生成结果、PDF 标注、每日复习和短剧制作仍待完善。
