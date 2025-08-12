<img width="1572" height="514" alt="image" src="https://github.com/user-attachments/assets/00178fd2-904b-44a3-a341-cd81e073d4f0" /># 简介
PyCharm 是由 JetBrains 公司开发的一款专门用于 **Python** 编程的集成开发环境（IDE）。

# 通义灵码

[菜鸟教程](https://www.runoob.com/pycharm/pycharm-ai-coding.html)

# 本地历史记录
PyCharm 自动记录文件修改历史（无需 Git）：

1. 右键文件 → 本地历史 → 显示历史（Local History → Show History）
<img width="1536" height="1060" alt="image" src="https://github.com/user-attachments/assets/94cfef4a-12d5-4e72-9b37-4ed1a3c65432" />

2. 可恢复任意时间点的版本
<img width="1430" height="510" alt="image" src="https://github.com/user-attachments/assets/6cf79bbc-46f2-45b8-920f-df9bf858106f" />

# 代码编辑
## 代码补全

| 补全类型       | 触发方式                          | 说明                           |
|----------------|-----------------------------------|--------------------------------|
| 基本补全       | Ctrl + Space (Win/Linux)          | 显示变量、函数、类等建议       |
|                | ⌘ + Space (Mac)                   |                                |
| 智能类型补全   | Ctrl + Shift + Space              | 根据上下文推荐更精准的类型     |
| 文件名补全     | 输入路径时自动触发                | 快速补全文件路径               |
| 动态模板补全   | 输入缩写（如 main + Tab）         | 快速生成代码片段（如 if __name__ ==...） |

## 快捷键与高效操作
常用快捷键速查表：

| 功能           | 快捷键 (Win/Linux) | 快捷键 (Mac) |
|----------------|--------------------|---------------|
| 复制当前行     | Ctrl + D           | ⌘ + D         |
| 删除当前行     | Ctrl + Y           | ⌘ + Delete    |
| 移动行         | Alt + Shift + ↑/↓  | ⌥ + ↑ + ↑/↓   |
| 快速修复建议   | Alt + Enter        | ⌥ + Enter     |
| 跳转到定义     | Ctrl + B           | ⌘ + B         |
| 查看参数提示   | Ctrl + P           | ⌘ + P         |

# 版本控制集成
PyCharm 提供了完整的 Git/GitHub 集成功能，让开发者可以直接在 IDE 中完成版本控制操作。

## 配置 Git/GitHub
- 打开 文件/PyCharm → 设置 → 版本控制 → Git
- 在 "Git 可执行文件路径" 中确认 PyCharm 已自动检测到 Git
- 点击 测试 按钮验证 Git 是否可用

<img width="2090" height="1422" alt="image" src="https://github.com/user-attachments/assets/7dc3fd93-a425-41a8-b90d-b2ea979bb010" />

## 配置用户信息
在终端运行：

```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## 集成 GitHub
1. 添加 GitHub 账户：
- 文件/PyCharm → 设置 → 版本控制 → GitHub
- 点击 + 添加账户
- 选择登录方式：
  - 通过 Github 登录：通过浏览器授权登录
  - 通过令牌登录：使用个人访问令牌
<img width="2090" height="1426" alt="image" src="https://github.com/user-attachments/assets/d52535cb-1c16-4c1f-a51c-5606dd6e6913" />

2. SSH 配置（可选）：
- 生成 SSH 密钥：ssh-keygen -t ed25519 -C "your_email@example.com"
- 将公钥添加到 GitHub 账户的 SSH keys 设置中

## 基本操作
我们可以在工具栏上的版本控制按钮创建 Git 仓库：
<img width="2140" height="894" alt="image" src="https://github.com/user-attachments/assets/254838f0-39f2-40af-8885-5435dc6d092a" />

之后项目上的版本控制按钮就会变成 master（主分支）：
<img width="1516" height="678" alt="image" src="https://github.com/user-attachments/assets/14c48b62-06b8-4865-8b12-02cb7e1610cd" />

## 提交与推送
在 提交工具窗口（Commit Tool Window）中：
- 勾选要提交的文件
- 输入提交信息
- 选择操作：
  - 提交（Commit）：仅本地提交
  - 提交并推送（Commit and Push）：提交后立即推送到远程

<img width="846" height="1402" alt="image" src="https://github.com/user-attachments/assets/de440330-68e0-481d-9cba-7cb29f6f9e4c" />

快捷键：

- 提交：Ctrl+K（Win/Linux） / ⌘K（Mac）

- 推送：Ctrl+Shift+K（Win/Linux） / ⌘⇧K（Mac）

**查看变更**

文件状态颜色标记：

- 蓝色：已修改

- 绿色：新增

- 灰色：未跟踪

- 红色：冲突

<img width="1572" height="514" alt="image" src="https://github.com/user-attachments/assets/fc6f0604-e500-4c7a-9c9f-84030c364e35" />

## 拉取与合并
### 拉取最新代码
1. Git → Pull 或 Ctrl+T（Win/Linux） / ⌘T（Mac）
2. 选择合并策略：
  - Merge：保留所有提交历史
  - Rebase：线性历史记录

### 合并分支
1. Git → 分支 → 合并分支
2. 选择要合并的目标分支
3. 解决可能的冲突

## 查看历史与差异
### 查看提交历史
1. Git → 显示历史 或 Alt+9

2. 功能：
- 查看文件/项目历史
- 比较不同版本
- 回滚到特定版本

### 比较差异
1. 文件差异：
- 右键文件 → Git → 比较与当前分支
- 或 Ctrl+D（Win/Linux） / ⌘D（Mac）

2. 行内差异：
- 修改的行会显示彩色标记
- 点击标记查看具体修改内容

