# DSH Chat Manager · 个人 fork / Personal fork

本仓库是 [WSL043/dsh-chat-manager](https://github.com/WSL043/dsh-chat-manager) 的个人 fork，
代码基线为上游 **v1.5.18**（2026-10-23 发布）。上游 MIT 许可证、作者署名与第三方许可说明均保留；
兼容性修复来自上游，本 fork 负责托管、验证与安装说明。

This repository is a personal fork of
[WSL043/dsh-chat-manager](https://github.com/WSL043/dsh-chat-manager), based on upstream
**v1.5.18** (published 2026-10-23). Upstream authorship, the MIT license, and third-party notices are preserved.

## 为什么需要这个 fork

DSH `0.2.1-rc.3` 在启动时会校验插件声明的内核范围。本地已安装的 `dsh-chat-manager@1.5.16`
只声明到 `0.2.1-rc.2`，因此被兼容性门禁直接跳过（插件页显示已安装，但界面无任何生效入口）：

```text
dsh: skipping profile bundle "dsh-chat-manager": Plugin dsh-chat-manager@1.5.16 is
incompatible with dsh 0.2.1-rc.3 ... Update the plugin or install a plugin version
compatible with this dsh runtime.
```

上游从 v1.5.17 起把兼容范围更新为官方最新五个内核，v1.5.18 是当前最新发布。本仓库即为该版本的
个人托管副本，可直接安装。

## 兼容性

| 项目 | 值 |
| --- | --- |
| 目标 DSH 内核 | `0.2.1-rc.3`、`0.2.1-rc.2`、`0.2.1-rc.1`、`0.2.1-alpha.5`、`0.2.1-alpha.4` |
| 验证环境 | Windows x64，DSH `0.2.1-rc.3`，`desktop` profile |
| 构建 | `pnpm run build` 通过 |
| 测试 | `pnpm test`：116/116 通过（基于 `@deepseek-ai/*@0.2.1-rc.3` 开发依赖） |
| 组合校验 | `dsh --profile <profile> --dump-config` 通过，`dsh-chat-manager` 不再被跳过 |

## 安装

DSH 插件页：**Plugins → Add plugin**，在“包名或地址”中填入固定版本：

```text
github:kzzzt/dsh-chat-manager#v1.5.18-fork.1
```

终端安装（固定版本；`desktop` profile 由 DSH Desktop 独占管理时请在插件页操作）：

```sh
dsh plugin --profile web add github:kzzzt/dsh-chat-manager#v1.5.18-fork.1
```

安装完成后重启 DSH，侧边栏标题处会出现归档入口，会话 **⋯** 菜单中会出现 **永久删除**。

## 与上游同步

```sh
git remote add upstream https://github.com/WSL043/dsh-chat-manager.git
git fetch upstream
git merge upstream/main
git push origin main
```

## 许可证

MIT，见 [LICENSE](LICENSE)、[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) 与 [SECURITY.md](SECURITY.md)。
本项目是非官方社区插件，与 DeepSeek 无隶属或背书关系。
