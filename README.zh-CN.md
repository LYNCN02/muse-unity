# Muse Unity

把 Meta Muse 接入 Unity 的独立开源包：C# 直连、手机蓝牙绑定、加密凭据存储、流式文字回复，以及可替换 ASR 的语音示例。无需本机桥接进程。

当前是 **0.1.0-preview.3 社区预览版**，不代表 Meta 或 Unity 官方产品。这里的 Muse 是 Meta 的个人智能体，不是 Unity 自带 AI 工具，也不是同名 EEG 头环。

## 关于 LYNOOK

[LYNOOK 官网](https://www.lynook.com/) · [公司 GitHub](https://github.com/LYNCN02)

LYNOOK 致力于让数字角色在你的桌面上拥有一个家。Project L 将双屏 3D 世界、可自定义角色与日常 AI 陪伴结合，探索数字角色融入现实生活的方式。

**Muse Unity 是完整开源的独立项目。** 本仓库公开接入代码、原生插件源码、示例生成器与测试工具，采用 [Apache-2.0](LICENSE)，同时保留上游和依赖的许可证。任何人都可以按许可证使用、学习、修改和再分发，包括商业使用。本接入项目没有闭源版本，也不要求购买 LYNOOK 硬件。

这里的开源范围是接入代码；Muse 与可选 ASR 服务仍有各自的访问条件和费用，使用者需自行提供凭据。

## 关于作者

[Jammie](https://someonewaits.com/) 正在打造 LYNOOK，将 3D 角色软件与 AI 交互带进实体设备，探索 AI 角色如何与人共享日常空间。他关注角色的身份、记忆、行为，以及对话之外持续存在的陪伴感。

个人网站 [Jammie's Digital Garden — someonewaits.com](https://someonewaits.com/) 记录了实体 AI、角色系统和 LYNOOK 的开发过程。Muse Unity 将其中一部分探索整理为完整开源的 Unity 接入项目，与社区共同分享和完善。

## 安装和使用

1. 使用 Unity 6，在 Package Manager 中通过 Git URL 安装：

   `https://github.com/LYNCN02/muse-unity.git#v0.1.0-preview.3`

2. 执行 `Tools > Muse Unity > Import TMP Essentials`，导入完成后执行 `Create sample scene` 和 `Open sample scene`，进入 Play Mode。
3. 点击 `Bind Muse`，填入自己的 Muse SDK Token。默认语音示例另需自己的 ElevenLabs Key，可在界面输入或通过 `ELEVENLABS_API_KEY` 环境变量提供。
4. 在手机 Muse App 开启开发者模式，用 `Settings > Devices > Add Device` 选择画面上的 `MuseGadget…`，授权后选择 `Use current connection`。
5. 单击 `Record` 后松开，讲话，再点 `Send`。达到 20 秒只停止录音并保留内容，等待明确发送；`Stop` 丢弃录音。

绑定后聊天不依赖蓝牙。下次启动点击 `Connect Muse`，凭据从 macOS Keychain / Android Keystore 恢复。独立包不读取其他应用的配置、Key 或绑定。

默认使用与 Muse App 相同的主对话，先订阅后发送，并按消息关联显示本次回复。识别音频发给 ASR 服务，只有识别结果文字发给 Muse。可通过 `Transcribe` 委托更换 ASR。

## 当前验证边界

- 独立包有全新 Unity 工程安装、协议/UI 隔离回归和原生编译验证，详见 [验证记录](Documentation~/validation.md)。
- 来源实现曾完成真实 iPad → Mac 绑定、凭据保存、Muse 连接和 ASR 文字提交；Muse App 中能看到回复。
- Unity 真实回复显示仍需完整验收，不能把模拟协议测试当作供应商服务验收。
- 一个 Android 16 → Mac 配对组合存在超过 GATT 512 字节限制的问题；Android/IL2CPP、macOS Player 尚未完整实机验收。
- 默认 TMP 字体覆盖有限。中文等语言请给 `MuseObjectFont` 指定合法可分发、覆盖目标字符的 TMP 字体。

欢迎贡献平台适配、真实设备验证和脱敏协议测试。所有源代码和依赖归属见 [NOTICE](NOTICE)，本项目采用 Apache-2.0；Muse 服务和 SDK Token 的使用仍受其服务条款约束。
