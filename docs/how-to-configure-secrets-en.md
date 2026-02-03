# 🔐 How to Find and Configure GitHub Secrets & Variables

This guide provides detailed instructions on how to find, configure, and manage Secrets (encrypted variables) and Variables (plain text variables) in your GitHub repository. This is a crucial step for running this project with GitHub Actions.

---

## 📋 Table of Contents

- [What are Secrets and Variables](#what-are-secrets-and-variables)
- [How to Access Configuration Page](#how-to-access-configuration-page)
- [Configure Secrets (Encrypted Variables)](#configure-secrets-encrypted-variables)
- [Configure Variables (Plain Text Variables)](#configure-variables-plain-text-variables)
- [View Configured Secrets and Variables](#view-configured-secrets-and-variables)
- [Modify or Delete Configuration](#modify-or-delete-configuration)
- [Common Questions](#common-questions)

---

## 🤔 What are Secrets and Variables

### Secrets (Encrypted Variables)
- **Purpose**: Store sensitive information (API Keys, passwords, tokens, etc.)
- **Features**:
  - Content is encrypted; cannot view original value after configuration
  - Automatically hidden in Actions logs
  - Suitable for all sensitive information
- **Examples**: `GEMINI_API_KEY`, `TELEGRAM_BOT_TOKEN`, `EMAIL_PASSWORD`

### Variables (Plain Text Variables)
- **Purpose**: Store non-sensitive configuration information
- **Features**:
  - Stored in plain text; can view and edit after configuration
  - Displayed normally in Actions logs
  - Suitable for public configuration items
- **Examples**: `STOCK_LIST`, `GEMINI_MODEL`, `REPORT_TYPE`

> ⚠️ **Important**: Configure sensitive information (like API Keys) in Secrets, and non-sensitive information (like stock list) in Variables.

---

## 🔍 How to Access Configuration Page

### Method 1: Access from Repository Homepage

1. **Open your forked repository homepage**
   - Visit `https://github.com/your-username/daily_stock_analysis`

2. **Click the `Settings` tab at the top**
   - Location: Navigation bar below repository name
   - Icon: ⚙️ Gear icon

3. **Find `Secrets and variables` in the left sidebar**
   - Location: Left sidebar, under `Security` section
   - Click to expand, then select `Actions`

4. **Enter the configuration page**
   - You will see two tabs:
     - **Secrets**: For configuring encrypted variables
     - **Variables**: For configuring plain text variables

### Method 2: Direct URL Access

Directly access the following URL in your browser (replace `your-username` with your GitHub username):

```
https://github.com/your-username/daily_stock_analysis/settings/secrets/actions
```

---

## 🔐 Configure Secrets (Encrypted Variables)

### Step 1: Enter Secrets Configuration Page

1. Follow the above method to enter `Settings` → `Secrets and variables` → `Actions`
2. Ensure you're on the **Secrets** tab

### Step 2: Add New Secret

1. **Click the `New repository secret` button**
   - Location: Top right of the page, green button

2. **Fill in Secret information**
   - **Name**: Enter the variable name, must exactly match the documentation
     - Examples: `GEMINI_API_KEY`, `TELEGRAM_BOT_TOKEN`
     - Naming rules: Uppercase letters, numbers, underscores; cannot start with a number
   
   - **Secret** (Value): Enter the actual API Key or password
     - Example: `AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXX` (Gemini API Key)
     - Note: Remove leading/trailing spaces when pasting

3. **Click `Add secret` button to save**

### Required Secrets Checklist

#### AI Model Configuration (At least one required)

| Secret Name | Description | How to Obtain |
|------------|-------------|---------------|
| `GEMINI_API_KEY` | Google Gemini API Key (Recommended, has free tier) | [Google AI Studio](https://aistudio.google.com/) |
| `OPENAI_API_KEY` | OpenAI Compatible API Key | Various service providers |
| `OPENAI_BASE_URL` | OpenAI Compatible API Address | e.g., `https://api.deepseek.com/v1` |

#### Notification Channel Configuration (At least one required)

| Secret Name | Description | How to Obtain |
|------------|-------------|---------------|
| `WECHAT_WEBHOOK_URL` | WeChat Work Webhook URL | WeChat Work Group → Group Bot → Add Bot |
| `FEISHU_WEBHOOK_URL` | Feishu Webhook URL | Feishu Group → Group Bot → Custom Bot |
| `TELEGRAM_BOT_TOKEN` | Telegram Bot Token | @BotFather → /newbot |
| `TELEGRAM_CHAT_ID` | Telegram Chat ID | @userinfobot or @RawDataBot |
| `EMAIL_SENDER` | Sender email address | e.g., `your_email@gmail.com` |
| `EMAIL_PASSWORD` | Email authorization code (not login password) | Gmail: App Password |
| `DISCORD_WEBHOOK_URL` | Discord Webhook URL | Discord Channel Settings → Integrations → Webhooks |
| `CUSTOM_WEBHOOK_URLS` | Custom Webhooks (comma-separated) | DingTalk, Slack, etc. |

#### Optional Secrets

| Secret Name | Description | How to Obtain |
|------------|-------------|---------------|
| `TAVILY_API_KEYS` | Tavily Search API (Recommended for news search) | [Tavily](https://tavily.com/) |
| `SERPAPI_API_KEYS` | SerpAPI Search API | [SerpAPI](https://serpapi.com/) |
| `BOCHA_API_KEYS` | Bocha Search API | [Bocha](https://open.bocha.cn/) |
| `TUSHARE_TOKEN` | Tushare Pro Token | [Tushare Pro](https://tushare.pro/) |
| `PUSHPLUS_TOKEN` | PushPlus Token | [PushPlus](https://www.pushplus.plus) |

---

## 📝 Configure Variables (Plain Text Variables)

### Step 1: Switch to Variables Tab

1. On the `Settings` → `Secrets and variables` → `Actions` page
2. Click the **Variables** tab (next to the Secrets tab)

### Step 2: Add New Variable

1. **Click the `New repository variable` button**
   - Location: Top right of the page, green button

2. **Fill in Variable information**
   - **Name**: Enter the variable name
     - Examples: `STOCK_LIST`, `GEMINI_MODEL`
   
   - **Value**: Enter the configuration value
     - Example: `600519,300750,002594` (Stock list)
     - Example: `gemini-2.0-flash` (Model name)

3. **Click `Add variable` button to save**

### Recommended Variables Checklist

| Variable Name | Description | Example Value | Required |
|--------------|-------------|---------------|----------|
| `STOCK_LIST` | Stock codes list (comma-separated) | `600519,300750,hk00700,AAPL` | ✅ Required |
| `GEMINI_MODEL` | Gemini model name | `gemini-2.0-flash` | Optional |
| `OPENAI_MODEL` | OpenAI model name | `deepseek-chat` | Optional |
| `REPORT_TYPE` | Report type | `simple` or `full` | Optional |
| `SINGLE_STOCK_NOTIFY` | Single stock notification mode | `true` or `false` | Optional |
| `ANALYSIS_DELAY` | Analysis delay (seconds) | `10` | Optional |
| `WECHAT_MSG_TYPE` | WeChat Work message type | `markdown` or `text` | Optional |

---

## 👀 View Configured Secrets and Variables

### View Secrets

1. Go to `Settings` → `Secrets and variables` → `Actions` → `Secrets` tab
2. You can see:
   - ✅ List of configured Secret names
   - ✅ Last update time for each Secret
   - ❌ **Cannot view actual values of Secrets** (this is a GitHub security feature)

### View Variables

1. Go to `Settings` → `Secrets and variables` → `Actions` → `Variables` tab
2. You can see:
   - ✅ List of configured Variable names
   - ✅ Actual values of each Variable
   - ✅ Last update time for each Variable

---

## ✏️ Modify or Delete Configuration

### Modify Secret

1. Find the Secret you want to modify in the Secrets list
2. Click the **Update** button on the right
3. Enter the new value
4. Click **Update secret** to save

> ⚠️ **Note**: You cannot view the current value; you can only overwrite it with a new value.

### Modify Variable

1. Find the Variable you want to modify in the Variables list
2. Click the **✏️ Edit icon** or **Update** button on the right
3. Modify the value
4. Click **Update variable** to save

### Delete Secret or Variable

1. Find the item you want to delete in the list
2. Click the **🗑️ Delete icon** or **Delete** button on the right
3. Confirm deletion

---

## ❓ Common Questions

### Q1: Can't find the Settings tab?

**Possible Reasons**:
- You don't have admin permissions for the repository
- You're viewing someone else's repository instead of your own forked copy

**Solution**:
1. Make sure you've **Forked** the repository to your own account
2. Visit `https://github.com/your-username/daily_stock_analysis`
3. If you're a collaborator, the repository owner needs to grant you Admin or Write permissions

### Q2: Configured Secret but Actions says it's undefined?

**Possible Reasons**:
- Secret/Variable name is misspelled
- Configured in the wrong location (e.g., Codespaces Secrets instead of Actions Secrets)

**Solution**:
1. Check if the Secret/Variable name exactly matches the documentation (case-sensitive)
2. Ensure configuration is under `Settings` → `Secrets and variables` → **Actions**
3. Re-run the workflow after configuration

### Q3: How do I know what should be Secrets vs Variables?

**Simple Rule**:
- **Contains sensitive information** → Secrets
  - API Keys, Tokens, passwords, Webhook URLs
  
- **Non-sensitive configuration** → Variables
  - Stock code lists, model names, switch options

**When unsure**: Use **Secrets** for better security.

### Q4: Do I need to re-run Actions after modifying a Secret?

**Yes**.
- After modifying configuration, the new value will be used in the next workflow run
- If you need immediate effect, manually trigger the workflow

### Q5: Can I see Secret values in Actions logs?

**No**.
- GitHub automatically replaces Secret values with `***` in logs
- This is a security feature to prevent sensitive information leakage
- For debugging, you can output partial characters (e.g., first 3 and last 3 characters)

### Q6: Is there a limit on the number of Secrets?

**Yes, there are limits**:
- Maximum 100 Secrets per repository
- Maximum 64 KB per Secret
- For this project, these limits are more than sufficient

---

## 🎯 Quick Checklist

After completing configuration, use this checklist to confirm:

### Minimal Configuration (Can Run)

- [ ] Configured AI model (`GEMINI_API_KEY` or `OPENAI_API_KEY`)
- [ ] Configured stock list (`STOCK_LIST`)
- [ ] Configured at least one notification channel
- [ ] Enabled GitHub Actions (Actions tab → Enable workflows)

### Recommended Configuration (Better Experience)

- [ ] Configured search API (`TAVILY_API_KEYS` or `SERPAPI_API_KEYS`)
- [ ] Configured multiple notification channels (WeChat + Email, etc.)
- [ ] Set `REPORT_TYPE=full` in Variables (full report)
- [ ] Manually tested one run (Actions → Run workflow)

---

## 📚 Related Documentation

- [Quick Start Guide](../README.md)
- [Full Configuration Guide](./full-guide.md)
- [FAQ](./FAQ.md)
- [Deployment Guide](./DEPLOY.md)

---

## 💡 Tips

1. **Use a password manager**: Recommend using 1Password, LastPass, etc. to manage API Keys
2. **Rotate keys regularly**: For security, consider rotating API Keys periodically
3. **Never hardcode in code**: Never write sensitive information into code and commit to Git
4. **Test configuration**: After adding configuration, manually run the workflow once to confirm
5. **Backup important configurations**: Back up API Keys locally in a secure location (don't commit to Git)

---

**Good luck with configuration! If you have questions, feel free to submit an [Issue](https://github.com/ZhuLinsen/daily_stock_analysis/issues).** 🎉
