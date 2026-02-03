# 🔐 如何查找和配置 GitHub Secrets 与 Variables

本指南详细介绍如何在 GitHub 仓库中查找、配置和管理 Secrets（加密变量）和 Variables（普通变量），这是使用 GitHub Actions 运行本项目的关键步骤。

---

## 📋 目录

- [什么是 Secrets 和 Variables](#什么是-secrets-和-variables)
- [如何访问配置页面](#如何访问配置页面)
- [配置 Secrets（加密变量）](#配置-secrets加密变量)
- [配置 Variables（普通变量）](#配置-variables普通变量)
- [查看已配置的 Secrets 和 Variables](#查看已配置的-secrets-和-variables)
- [修改或删除配置](#修改或删除配置)
- [常见问题](#常见问题)

---

## 🤔 什么是 Secrets 和 Variables

### Secrets（加密变量）
- **用途**：存储敏感信息（API Keys、密码、Token 等）
- **特点**：
  - 内容加密存储，配置后无法查看原值
  - 在 Actions 日志中自动隐藏
  - 适合存储所有敏感信息
- **示例**：`GEMINI_API_KEY`、`TELEGRAM_BOT_TOKEN`、`EMAIL_PASSWORD`

### Variables（普通变量）
- **用途**：存储非敏感配置信息
- **特点**：
  - 明文存储，配置后可以查看和编辑
  - 在 Actions 日志中正常显示
  - 适合存储公开的配置项
- **示例**：`STOCK_LIST`、`GEMINI_MODEL`、`REPORT_TYPE`

> ⚠️ **重要提示**：将敏感信息（如 API Key）配置到 Secrets 中，非敏感信息（如股票列表）配置到 Variables 中。

---

## 🔍 如何访问配置页面

### 方法一：通过仓库主页访问

1. **打开你 Fork 的仓库主页**
   - 访问 `https://github.com/你的用户名/daily_stock_analysis`

2. **点击顶部的 `Settings` 选项卡**
   - 位置：仓库名称下方的导航栏
   - 图标：⚙️ 齿轮图标

3. **在左侧菜单中找到 `Secrets and variables`**
   - 位置：左侧边栏，`Security` 部分
   - 点击展开后选择 `Actions`

4. **进入配置页面**
   - 你会看到两个标签：
     - **Secrets**：用于配置加密变量
     - **Variables**：用于配置普通变量

### 方法二：直接访问 URL

直接在浏览器中访问以下地址（替换 `你的用户名` 为你的 GitHub 用户名）：

```
https://github.com/你的用户名/daily_stock_analysis/settings/secrets/actions
```

---

## 🔐 配置 Secrets（加密变量）

### 步骤 1：进入 Secrets 配置页面

1. 按照上述方法进入 `Settings` → `Secrets and variables` → `Actions`
2. 确保当前在 **Secrets** 标签下

### 步骤 2：添加新的 Secret

1. **点击 `New repository secret` 按钮**
   - 位置：页面右上角，绿色按钮

2. **填写 Secret 信息**
   - **Name**（名称）：输入变量名称，必须与配置文档中的名称完全一致
     - 示例：`GEMINI_API_KEY`、`TELEGRAM_BOT_TOKEN`
     - 命名规则：大写字母、数字、下划线，不能以数字开头
   
   - **Secret**（值）：输入实际的 API Key 或密码
     - 示例：`AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXX`（Gemini API Key）
     - 注意：粘贴时去除首尾空格

3. **点击 `Add secret` 按钮保存**

### 必须配置的 Secrets 清单

#### AI 模型配置（至少配置一个）

| Secret 名称 | 说明 | 如何获取 |
|------------|------|---------|
| `GEMINI_API_KEY` | Google Gemini API Key（推荐，有免费额度） | [Google AI Studio](https://aistudio.google.com/) |
| `OPENAI_API_KEY` | OpenAI 兼容 API Key | 各服务商官网 |
| `OPENAI_BASE_URL` | OpenAI 兼容 API 地址 | 如 `https://api.deepseek.com/v1` |

#### 通知渠道配置（至少配置一个）

| Secret 名称 | 说明 | 如何获取 |
|------------|------|---------|
| `WECHAT_WEBHOOK_URL` | 企业微信 Webhook URL | 企业微信群 → 群机器人 → 添加机器人 |
| `FEISHU_WEBHOOK_URL` | 飞书 Webhook URL | 飞书群 → 群机器人 → 自定义机器人 |
| `TELEGRAM_BOT_TOKEN` | Telegram Bot Token | @BotFather → /newbot |
| `TELEGRAM_CHAT_ID` | Telegram Chat ID | @userinfobot 或 @RawDataBot |
| `EMAIL_SENDER` | 发件人邮箱 | 如 `your_email@qq.com` |
| `EMAIL_PASSWORD` | 邮箱授权码（非登录密码） | QQ邮箱：设置 → 账户 → POP3/SMTP → 获取授权码 |
| `DISCORD_WEBHOOK_URL` | Discord Webhook URL | Discord频道设置 → 集成 → Webhook |
| `CUSTOM_WEBHOOK_URLS` | 自定义 Webhook（多个用逗号分隔） | 钉钉、Slack 等服务 |

#### 可选 Secrets

| Secret 名称 | 说明 | 如何获取 |
|------------|------|---------|
| `TAVILY_API_KEYS` | Tavily 搜索 API（推荐，用于新闻搜索） | [Tavily](https://tavily.com/) |
| `SERPAPI_API_KEYS` | SerpAPI 搜索 API | [SerpAPI](https://serpapi.com/) |
| `BOCHA_API_KEYS` | 博查搜索 API | [博查搜索](https://open.bocha.cn/) |
| `TUSHARE_TOKEN` | Tushare Pro Token | [Tushare Pro](https://tushare.pro/) |
| `PUSHPLUS_TOKEN` | PushPlus Token | [PushPlus](https://www.pushplus.plus) |

---

## 📝 配置 Variables（普通变量）

### 步骤 1：切换到 Variables 标签

1. 在 `Settings` → `Secrets and variables` → `Actions` 页面
2. 点击 **Variables** 标签（位于 Secrets 标签旁边）

### 步骤 2：添加新的 Variable

1. **点击 `New repository variable` 按钮**
   - 位置：页面右上角，绿色按钮

2. **填写 Variable 信息**
   - **Name**（名称）：输入变量名称
     - 示例：`STOCK_LIST`、`GEMINI_MODEL`
   
   - **Value**（值）：输入配置值
     - 示例：`600519,300750,002594`（股票列表）
     - 示例：`gemini-2.0-flash`（模型名称）

3. **点击 `Add variable` 按钮保存**

### 建议配置的 Variables 清单

| Variable 名称 | 说明 | 示例值 | 是否必填 |
|--------------|------|--------|---------|
| `STOCK_LIST` | 自选股代码列表（逗号分隔） | `600519,300750,hk00700,AAPL` | ✅ 必填 |
| `GEMINI_MODEL` | Gemini 模型名称 | `gemini-2.0-flash` | 可选 |
| `OPENAI_MODEL` | OpenAI 模型名称 | `deepseek-chat` | 可选 |
| `REPORT_TYPE` | 报告类型 | `simple` 或 `full` | 可选 |
| `SINGLE_STOCK_NOTIFY` | 单股推送模式 | `true` 或 `false` | 可选 |
| `ANALYSIS_DELAY` | 分析延迟（秒） | `10` | 可选 |
| `WECHAT_MSG_TYPE` | 企业微信消息类型 | `markdown` 或 `text` | 可选 |

---

## 👀 查看已配置的 Secrets 和 Variables

### 查看 Secrets

1. 进入 `Settings` → `Secrets and variables` → `Actions` → `Secrets` 标签
2. 你可以看到：
   - ✅ 已配置的 Secret 名称列表
   - ✅ 每个 Secret 的最后更新时间
   - ❌ **无法查看 Secret 的实际值**（这是 GitHub 的安全特性）

### 查看 Variables

1. 进入 `Settings` → `Secrets and variables` → `Actions` → `Variables` 标签
2. 你可以看到：
   - ✅ 已配置的 Variable 名称列表
   - ✅ 每个 Variable 的实际值
   - ✅ 每个 Variable 的最后更新时间

---

## ✏️ 修改或删除配置

### 修改 Secret

1. 在 Secrets 列表中找到要修改的 Secret
2. 点击右侧的 **Update** 按钮
3. 输入新的值
4. 点击 **Update secret** 保存

> ⚠️ **注意**：无法查看当前值，只能用新值覆盖。

### 修改 Variable

1. 在 Variables 列表中找到要修改的 Variable
2. 点击右侧的 **✏️ 编辑图标** 或 **Update** 按钮
3. 修改值
4. 点击 **Update variable** 保存

### 删除 Secret 或 Variable

1. 在列表中找到要删除的项
2. 点击右侧的 **🗑️ 删除图标** 或 **Delete** 按钮
3. 确认删除

---

## ❓ 常见问题

### Q1: 找不到 Settings 选项卡？

**可能原因**：
- 你没有该仓库的管理员权限
- 你在查看别人的仓库而不是自己 Fork 的仓库

**解决方案**：
1. 确保你已经 **Fork** 了仓库到自己的账号下
2. 访问的是 `https://github.com/你的用户名/daily_stock_analysis`
3. 如果是协作者，需要仓库所有者授予 Admin 或 Write 权限

### Q2: 配置了 Secret 但 Actions 运行时提示未定义？

**可能原因**：
- Secret/Variable 名称拼写错误
- 配置到了错误的位置（比如配置到了 Codespaces Secrets 而不是 Actions Secrets）

**解决方案**：
1. 检查 Secret/Variable 名称是否与文档完全一致（区分大小写）
2. 确保在 `Settings` → `Secrets and variables` → **Actions** 下配置
3. 配置后重新运行 workflow

### Q3: 如何知道哪些应该配置为 Secrets，哪些应该配置为 Variables？

**简单规则**：
- **包含敏感信息的** → Secrets
  - API Keys、Tokens、密码、Webhook URLs
  
- **非敏感的配置项** → Variables
  - 股票代码列表、模型名称、开关选项

**不确定时**：优先使用 **Secrets**，更安全。

### Q4: 修改 Secret 后需要重新运行 Actions 吗？

**是的**。
- 修改配置后，下次运行 workflow 时会自动使用新值
- 如果需要立即生效，手动触发一次 workflow

### Q5: 可以在 Actions 日志中看到 Secret 的值吗？

**不可以**。
- GitHub 会自动将 Secret 的值在日志中替换为 `***`
- 这是安全特性，防止敏感信息泄露
- 如果需要调试，可以输出部分字符（如前3位后3位）

### Q6: Secret 有数量限制吗？

**有限制**：
- 每个仓库最多 100 个 Secrets
- 每个 Secret 最大 64 KB
- 对于本项目来说，远远够用

---

## 🎯 快速检查清单

完成配置后，使用此清单确认：

### 最小化配置（能运行）

- [ ] 已配置 AI 模型（`GEMINI_API_KEY` 或 `OPENAI_API_KEY`）
- [ ] 已配置自选股列表（`STOCK_LIST`）
- [ ] 已配置至少一个通知渠道
- [ ] 已启用 GitHub Actions（Actions 标签 → Enable workflows）

### 推荐配置（更好的体验）

- [ ] 已配置搜索 API（`TAVILY_API_KEYS` 或 `SERPAPI_API_KEYS`）
- [ ] 已配置多个通知渠道（企业微信 + 邮件等）
- [ ] 已在 Variables 中设置 `REPORT_TYPE=full`（完整报告）
- [ ] 已手动测试运行一次（Actions → Run workflow）

---

## 📚 相关文档

- [快速开始指南](../README.md)
- [完整配置指南](./full-guide.md)
- [常见问题解答](./FAQ.md)
- [部署指南](./DEPLOY.md)

---

## 💡 小贴士

1. **使用密码管理器**：建议使用 1Password、LastPass 等工具管理 API Keys
2. **定期轮换密钥**：出于安全考虑，建议定期更换 API Keys
3. **不要在代码中硬编码**：永远不要将敏感信息写入代码并提交到 Git
4. **测试配置**：添加配置后，先手动运行一次 workflow 确认无误
5. **备份重要配置**：在本地安全位置备份 API Keys（不要提交到 Git）

---

**祝配置顺利！如有问题，欢迎提交 [Issue](https://github.com/ZhuLinsen/daily_stock_analysis/issues)。** 🎉
