# 简介（2025-08-08）
Visual Studio Code（简称VS Code）是由微软开发的一个现代化、轻量级的代码编辑器，它支持几十种主流编程语言（如 JavaScript、Python、C++、Java、Go 等），并通过扩展提供更广泛的语言支持。

VSCode 可以在 Windows、macOS 和 Linux 操作系统上运行，为开发者提供了一个统一的开发环境。

# 版本类型
以下是 Visual Studio Code 的主要版本类型及其特点对比：

| 版本名称       | 下载渠道          | 许可协议         | 主要特点                                                     | 适合人群                           |
| -------------- | ----------------- | ---------------- | ------------------------------------------------------------ | ---------------------------------- |
| 官方版         | 微软官网          | 微软专有许可协议 | - 官方支持<br>- 带有微软品牌和服务<br>- 内置遥测功能         | 需要稳定功能的普通用户和开发者     |
| 开源版（Code - OSS） | GitHub 源码       | MIT 许可协议     | - 完全开源<br>- 无微软品牌和遥测功能<br>- 需要手动构建       | 开源爱好者或对隐私有高要求的用户   |
| VSCodium       | VSCodium 官网     | MIT 许可协议     | - 基于 Code - OSS 构建<br>- 去掉微软遥测功能<br>- 即装即用     | 需要无遥测的开源版本的用户         |
| Insiders 版    | VS Code Insiders  | 微软专有许可协议 | - 最新特性预览<br>- 每日构建，可能存在不稳定性               | 喜欢尝鲜的开发者，测试版功能用户   |
| 社区构建版     | 各开源社区提供    | 各社区指定协议   | - 根据 Code - OSS 修改<br>- 添加社区特色功能                  | 需要特定功能或自定义版本的用户     |

# windows安装
VS Code 官方网站下载页面：https://code.visualstudio.com/Download。

[教程](https://www.runoob.com/vscode/vscode-windows-install.html)

# linux安装
[教程](https://www.runoob.com/vscode/vscode-linux-install.html)

# 在 VS Code 中安装 TONGYI Lingma（通义灵码） 扩展
TONGYI Lingma（通义灵码） 是阿里云推出的一款智能编程助手，基于通义大模型开发，旨在帮助开发者提高编程效率。

通义灵码支持多种编程语言，能够提供代码补全、代码解释、代码优化、智能问答等功能。

官方说明参见：https://lingma.aliyun.com/。

- 打开 Visual Studio Code 扩展窗口，搜索 TONGYI Lingma，找到通义灵码后单击安装。
- 安装完成后，请重启 Visual Studio Code。
- 重启 Visual Studio Code 后，单击侧边导航的通义灵码，在通义灵码助手的窗口单击登录按钮。
- 按住扩展图标的按钮，直接拖动到右侧，把 AI 编程功能放到右边

# 终端
终端快捷键：

| 功能         | Windows/Linux    | macOS            |
| ------------ | ---------------- | ---------------- |
| 显示集成终端 | Ctrl + `         | Ctrl + `         |
| 新建终端     | Ctrl+Shift+`     | Cmd+Shift+`      |
| 切换终端     | Ctrl+PageUp/PageDown | Cmd+PageUp/PageDown |
| 关闭终端     | Ctrl+Shift+W     | Cmd+Shift+W      |

## 与命令输出交互
VS Code 中的终端还提供了与命令输出交互的功能，命令通常会输出文件路径或 URL，你可能希望直接打开或跳转到这些链接。

例如，编译器或代码检查工具可能会返回一个包含文件路径和行号的错误信息。你不需要手动去搜索该文件，只需在终端输出中选择该链接即可直接在编辑器中打开文件。

让我们看看如何与终端中的命令输出进行交互：

1. 打开你之前运行过 ls 或 dir 命令的终端。
2. 在终端中，按住 Ctrl/Cmd 键，将鼠标悬停在文件名上，然后选择该链接。

## 浏览历史命令
在使用终端时，我们可能需要查看之前的命令及其输出，或者可能想重新运行某个命令。按下 Ctrl + ↑ ，向上滚动至终端历史记录中的上一条命令。

# 命令
Windows/Linux 快捷键: Ctrl + Shift + P

## 命令面板的操作模式
命令面板支持多种操作模式，根据输入内容呈现不同功能：

输入 > 符号后：开始输入以过滤命令列表。

例如，输入 move terminal，可以找到将终端移动到新窗口的相关命令。
<img width="787" height="349" alt="image" src="https://github.com/user-attachments/assets/0a1a5875-123a-440e-b529-015c09e5f191" />

删除 > 符号后：输入内容将搜索工作区中的文件。
<img width="1920" height="1046" alt="image" src="https://github.com/user-attachments/assets/814f63d1-7b29-47ac-8eb8-1b44f4d67d08" />

# 设置
配置 VS Code 的两种方式：

- 使用设置编辑器（Settings Editor） 修改设置。
- 直接编辑 settings.json 文件。

使用快捷键打开设置页面：Windows/Linux 快捷键: Ctrl + ,

# 调试
打断点快捷键：F9

调试快捷键：F5

# 快捷键
快捷键的设置可以通过菜单栏的 Code > 首选项 > 键盘快捷方式 查看。

1. 通用操作

| 功能               | Windows/Linux         | macOS                 |
| ------------------ | --------------------- | --------------------- |
| 打开命令面板       | Ctrl + Shift + P      | Cmd + Shift + P       |
| 打开设置           | Ctrl + ,              | Cmd + ,               |
| 打开终端           | Ctrl + `              | Ctrl + `              |
| 新建窗口           | Ctrl + Shift + N      | Cmd + Shift + N       |
| 关闭窗口           | Ctrl + Shift + W      | Cmd + Shift + W       |
| 保存文件           | Ctrl + S              | Cmd + S               |
| 全部保存           | Ctrl + K S            | Cmd + Option + S      |
| 自动保存切换       | Ctrl + Shift + P 后搜索 Auto Save | 同左                  |
| 快速打开，转到文件 | Ctrl + P              | Cmd + P               |
| 键盘快捷键设置     | Ctrl + K, Ctrl + S    | Cmd + K, Cmd + S      |

2. 文件与编辑器

| 功能               | Windows/Linux      | macOS            |
| ------------------ | ------------------ | ---------------- |
| 新建文件           | Ctrl + N           | Cmd + N          |
| 打开文件           | Ctrl + O           | Cmd + O          |
| 保存文件           | Ctrl + S           | Cmd + S          |
| 另存为             | Ctrl + Shift + S   | Cmd + Shift + S  |
| 关闭文件           | Ctrl + W           | Cmd + W          |
| 关闭所有文件       | Ctrl + K, Ctrl + W | Cmd + K, Cmd + W |
| 重新打开关闭的文件 | Ctrl + Shift + T   | Cmd + Shift + T  |
| 打开文件夹         | Ctrl+K O           | Cmd+K O          |
| 上一个文件         | Ctrl+Tab           | Cmd+Tab          |
| 下一个文件         | Ctrl+Shift+Tab     | Cmd+Shift+Tab    |
| 切换编辑器布局     | Alt+Shift+数字     | Cmd+Option+数字  |
| 全屏切换           | F11                | Ctrl+Cmd+F      |

3. 代码编辑

| 功能         | Windows/Linux      | macOS            |
| ------------ | ------------------ | ---------------- |
| 撤销         | Ctrl + Z           | Cmd + Z          |
| 重做         | Ctrl + Y           | Cmd + Y          |
| 复制         | Ctrl + C           | Cmd + C          |
| 剪切         | Ctrl + X           | Cmd + X          |
| 粘贴         | Ctrl + V           | Cmd + V          |
| 查找         | Ctrl + F           | Cmd + F          |
| 替换         | Ctrl + H           | Cmd + H          |
| 全选         | Ctrl + A           | Cmd + A          |
| 格式化代码   | Shift + Alt + F    | Shift + Option + F |
| 注释行       | Ctrl + /           | Cmd + /          |
| 多行注释     | Shift + Alt + A    | Shift + Option + A |
| 复制当前行   | Alt + Shift + Down | Option + Shift + Down |
| 删除当前行   | Ctrl + Shift + K   | Cmd + Shift + K  |
| 移动当前行   | Alt + Up/Down      | Option + Up/Down |
| 选中当前行   | Ctrl + L           | Cmd + L          |
| 查找替换     | Ctrl + H           | Cmd + Option + F |
| 转到行号     | Ctrl + G           | Cmd + G          |
| 在下方插入行 | Ctrl + Enter       | Cmd + Enter      |
| 在上方插入行 | Ctrl + Shift + Enter | Cmd + Shift + Enter |
| 跳转到匹配的括号 | Ctrl + Shift + \  | Cmd + Shift + \  |
| 缩进/取消缩进 | Ctrl + ] / [       | Cmd + ] / [      |
| 转到行首/行尾 | Home / End         | Cmd + ← / →      |
| 转到文件开头/结尾 | Ctrl + Home / End | Cmd + ↑ / ↓      |
| 折叠/展开区域 | Ctrl + Shift + [ / ] | Option + Cmd + [ / ] |
| 切换块注释   | Shift + Alt + A    | Option + Shift + A |
| 切换自动换行 | Alt + Z            | Option + Z       |

4. 多光标操作

| 功能               | Windows/Linux         | macOS                |
| ------------------ | --------------------- | -------------------- |
| 插入光标           | Alt + 点击            | Option + 点击        |
| 在上方/下方插入光标 | Ctrl + Alt + ↑ / ↓    | Option + Cmd + ↑ / ↓ |
| 撤销上一个光标操作 | Ctrl + U              | Cmd + U              |
| 选择当前行         | Ctrl + L              | Cmd + L              |
| 选择所有匹配项     | Ctrl + F2             | Cmd + F2             |
| 列选择             | Shift + Alt + 拖动    | Shift + Option + 拖动|
| 选中所有匹配内容   | Ctrl + Shift + L      | Cmd + Shift + L      |
| 选中下一个匹配     | Ctrl + D              | Cmd + D              |

5. 调试

| 功能     | Windows/Linux | macOS    |
| -------- | ------------- | -------- |
| 开始调试 | F5            | F5       |
| 停止调试 | Shift+F5      | Shift+F5 |
| 步过     | F10           | F10      |
| 步入     | F11           | F11      |
| 步出     | Shift+F11     | Shift+F11 |
| 切换断点 | F9            | F9       |

6. 搜索和导航

| 功能               | Windows/Linux     | macOS             |
| ------------------ | ----------------- | ----------------- |
| 全局搜索           | Ctrl+Shift+F      | Cmd+Shift+F       |
| 转到定义           | F12               | F12               |
| 转到声明           | Ctrl+F12          | Cmd+F12           |
| 查找引用           | Shift+F12         | Shift+F12         |
| 显示大纲           | Ctrl+Shift+O      | Cmd+Shift+O       |
| 跳转到上一个位置   | Ctrl+Alt+Left     | Cmd+Option+Left   |
| 跳转到下一个位置   | Ctrl+Alt+Right    | Cmd+Option+Right  |

7. 版本控制

| 功能               | Windows/Linux | macOS         |
| ------------------ | ------------- | ------------- |
| 打开版本控制视图 | Ctrl+Shift+G  | Cmd+Shift+G   |
| 提交代码         | Ctrl+Enter    | Cmd+Enter     |
| 查看变更         | Ctrl+Shift+D  | Cmd+Shift+D   |

8. 终端操作

| 功能         | Windows/Linux    | macOS            |
| ------------ | ---------------- | ---------------- |
| 显示集成终端 | Ctrl + `         | Ctrl + `         |
| 新建终端     | Ctrl+Shift+`     | Cmd+Shift+`      |
| 切换终端     | Ctrl+PageUp/PageDown | Cmd+PageUp/PageDown |
| 关闭终端     | Ctrl+Shift+W     | Cmd+Shift+W      |

9. 命令面板

| 操作               | Windows/Linux    | macOS            |
| ------------------ | ---------------- | ---------------- |
| 打开命令面板       | Ctrl + Shift + P | Cmd + Shift + P  |
| 打开键盘快捷键参考 | Ctrl + K, Ctrl + S | Cmd + K, Cmd + S |

10. 显示

| 功能             | Windows/Linux    | macOS            |
| ---------------- | ---------------- | ---------------- |
| 切换全屏         | F11              | Cmd + Ctrl + F   |
| 放大/缩小        | Ctrl + = / -     | Cmd + = / -      |
| 切换侧边栏可见性 | Ctrl + B         | Cmd + B          |
| 显示资源管理器   | Ctrl + Shift + E | Cmd + Shift + E  |
| 显示搜索         | Ctrl + Shift + F | Cmd + Shift + F  |
| 显示源代码控制   | Ctrl + Shift + G | Cmd + Shift + G  |
| 显示调试         | Ctrl + Shift + D | Cmd + Shift + D  |
| 显示扩展         | Ctrl + Shift + X | Cmd + Shift + X  |

11. 扩展操作

| 操作     | Windows/Linux               | macOS       |
| -------- | --------------------------- | ----------- |
| 安装扩展 | Ctrl + Shift + X            | Cmd + Shift + X |
| 扩展管理 | Ctrl + Shift + P → 输入 "Extensions" | 同左        |

12. 其他

| 功能             | Windows/Linux   | macOS       |
| ---------------- | --------------- | ----------- |
| 打开 Markdown 预览 | Ctrl + K, V     | Cmd + K, V  |
| 禅模式           | Ctrl + K, Z     | Cmd + K, Z  |

## 官方提供的快捷键说明
### windows
<img width="2102" height="1608" alt="image" src="https://github.com/user-attachments/assets/83f196ce-64a7-40be-b892-129f93ff785e" />
### linux
<img width="2112" height="1608" alt="image" src="https://github.com/user-attachments/assets/860f6084-a1ec-4ddd-b800-9fe3ecdbddf5" />
### mac
<img width="2108" height="1606" alt="image" src="https://github.com/user-attachments/assets/2c2d7703-abe3-4721-9f63-607fe02b746c" />

# 
