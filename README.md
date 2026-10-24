![>.< 封面：macOS 划词、截图与输入翻译工具](docs/images/cover.svg)

# >.<

>.< 是一款轻量的 macOS 中英翻译工具。选中文字、框选屏幕或直接输入，译文都会显示在桌面浮窗中。可使用苹果系统翻译，也可接入 DeepSeek 或自定义模型服务。

## 看看效果

翻译浮窗可切换语言方向、复制译文并保持置顶；历史记录和收藏保存在本机。

![翻译浮窗](docs/images/translation.png)

在服务设置中选择苹果系统翻译、DeepSeek 或支持 OpenAI Chat Completions 格式的接口。

![翻译服务设置](docs/images/services.png)

## 怎么使用

| 操作 | 默认快捷键 | 说明 |
| --- | --- | --- |
| 划词翻译 | Control + D | 在其他应用中选中文字后按快捷键 |
| 截图翻译 | Control + S | 框选区域，本机识别文字后翻译；Esc 取消 |
| 输入翻译 | Control + A | 输入文字后按 Enter 翻译，Shift + Enter 换行 |

关闭窗口后，快捷键仍可使用；点击 Dock 图标可重新打开窗口。按 **Command + Q** 退出。

## 从源码运行

需要 macOS 14 或更高版本，以及带有 macOS 15 或更新 SDK 的 Swift 6 工具链。苹果系统翻译需要 macOS 15 或更高版本；macOS 14 可配置 DeepSeek 或自定义 API。

```sh
git clone https://github.com/MN0709/OvO.git
cd OvO
./scripts/build-app.sh
open 'dist/>.<.app'
```

构建脚本会在本机生成开发签名。首次打开时，若 macOS 提示阻止，请在「系统设置 → 隐私与安全性」中确认打开；无需关闭系统安全保护。当前未提供经过 Apple 公证的安装包。构建细节见 [开发说明](docs/DEVELOPMENT.md)。

## 服务与数据

| 项目 | 说明 |
| --- | --- |
| 苹果系统翻译 | macOS 15+，无需 API Key；首次使用可能需要下载中英文语言包 |
| DeepSeek / 自定义 API | 在应用内填写服务配置；费用由所选服务商决定 |
| 划词 / 截图权限 | 按 macOS 提示授予辅助功能或屏幕录制权限；仅输入翻译无需这两项权限 |
| API Key | 保存在 macOS 钥匙串中 |
| 历史与收藏 | 只保存在本机，可在应用内关闭自动保存或删除记录 |

截图文字由 Apple Vision 在本机识别。使用远程模型服务时，待翻译文字会发送到你配置的服务地址；使用苹果系统翻译时不需要模型 API。自定义 API 支持兼容 OpenAI Chat Completions 的 HTTPS 服务，以及本机 HTTP 服务。

## 开发与反馈

运行 `./scripts/test.sh` 执行测试。欢迎在 [Issues](https://github.com/MN0709/OvO/issues) 反馈问题；请附上 macOS 版本、芯片型号和复现步骤，避免上传密钥或私人翻译内容。

源码采用 [MIT License](LICENSE)。
