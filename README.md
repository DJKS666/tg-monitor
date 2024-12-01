# Telegram 消息监控程序 

## 项目简介 
本项目是一个基于 Python 的 Telegram 消息监控程序，利用 `Telethon` 库与 Telegram API 进行交互。程序可以监控指定对话中的消息，根据关键词、正则表达式或文件后缀名进行匹配，自动执行转发、邮件通知等操作。此外，程序还支持定时发送消息等功能。
## 功能特性 
 
- **关键词监控** ：根据指定的关键词或正则表达式，监控特定对话中的消息。
 
- **文件监控** ：根据指定的文件后缀名，监控特定对话中的文件消息。
 
- **自动转发** ：当检测到匹配的消息时，自动将消息转发到指定的目标对话。
 
- **邮件通知** ：当检测到匹配的消息时，发送邮件通知。
 
- **定时消息** ：使用 Cron 表达式定时发送消息到指定对话。
 
- **用户过滤** ：可根据用户 ID、用户名或昵称，指定需要监控的用户。
 
- **日志记录** ：记录程序运行过程中的重要事件和错误信息。

## 环境要求 

- Python 3.7 及以上版本
 
- Telegram API 凭证（`api_id` 和 `api_hash`）
 
- 需要安装以下 Python 库： 
  - `telethon`
 
  - `asyncio`
 
  - `pytz`
 
  - `apscheduler`
    
## 安装指南 
 
1. **克隆或下载项目代码** ：

```bash
git clone https://github.com/DJKS666/tg-monitor.git
```
 
2. **安装依赖库** ：

```bash
pip install -r -requirements.txt
```
如果您使用的是 `pipenv` 或 `conda`，请根据相应的工具安装依赖库。
 
3. **获取 Telegram API 凭证** ： 
  - 前往 [Telegram 官方网站]()  创建您的应用，获取 `api_id` 和 `api_hash`。
 
4. **配置邮件服务器（可选）** ：
  - 如果您需要使用邮件通知功能，请在代码中配置 SMTP 服务器信息和发件人、收件人邮箱。
```bash    
SMTP_SERVER = "smtp.qq.com"          # SMTP 服务器，例如 QQ 邮箱
SMTP_PORT = 465                      # SMTP 端口，通常为 465
SENDER_EMAIL = "您的邮箱@example.com"  # 发件人邮箱
EMAIL_PASSWORD = "您的邮箱授权码"      # 邮箱授权码或密码
RECIPIENT_EMAIL = "收件人邮箱@example.com"  # 收件人邮箱
```

## 使用说明 
 
1. **运行程序** ：
在终端或命令行中，导航到项目目录，运行以下命令：


```bash
python monitor.py
```
 
2. **登录 Telegram** ： 
  - 程序首次运行时，会提示您输入 `api_id` 和 `api_hash`。
 
  - 输入您的 Telegram 手机号（格式如 `+8613800138000`），然后根据提示输入收到的验证码。

  - 如果您的账号启用了两步验证，需输入密码。
 
3. **设置监控参数** ：
  - 程序启动后，会显示可用命令列表。

  - 您可以根据需要添加关键词、文件后缀名监控、定时消息等配置。
 
4. **启动监控** ： 
  - 在完成配置后，输入命令 `start` 启动监控。

  - 程序会根据您设置的规则，监控指定对话中的消息。

## 命令列表 

以下是在程序中可用的命令列表：
 
1. **list**  - 列出所有对话

```plaintext
列出您的 Telegram 账号中的所有对话，包括群组和频道，显示其名称和 ID。
```
 
2. **addkeyword**  - 添加关键词

```plaintext
添加需要监控的关键词或正则表达式，以及相关配置，如监听的对话 ID、用户、自动转发目标等。
```
 
3. **modifykeyword**  - 修改关键词

```plaintext
修改已添加的关键词的配置，如更改关键词内容、监听的对话、自动转发设置等。
```
 
4. **removekeyword**  - 移除关键词

```plaintext
从关键词监控列表中移除指定的关键词。
```
 
5. **showkeywords**  - 显示所有关键词及其配置

```plaintext
列出当前已添加的所有关键词及其对应的配置。
```
 
6. **addext**  - 添加文件后缀名监控

```plaintext
添加需要监控的文件后缀名，以及相关配置。
```
 
7. **modifyext**  - 修改文件后缀名监控

```plaintext
修改已添加的文件后缀名监控的配置。
```
 
8. **removeext**  - 移除文件后缀名监控

```plaintext
从文件后缀名监控列表中移除指定的后缀名。
```
 
9. **showext**  - 显示所有文件后缀名及其配置

```plaintext
列出当前已添加的所有文件后缀名及其对应的配置。
```
 
10. **schedule**  - 添加定时消息

```plaintext
使用 Cron 表达式添加定时发送的消息。
```
 
11. **modifyschedule**  - 修改定时消息

```plaintext
修改已添加的定时消息的配置。
```
 
12. **removeschedule**  - 删除定时消息

```plaintext
删除指定的定时消息。
```
 
13. **showschedule**  - 显示所有定时消息

```plaintext
列出当前已添加的所有定时消息及其配置。
```
 
14. **start**  - 开始监控

```plaintext
开始监控，根据已设置的配置监听消息。
```
 
15. **stop**  - 停止监控

```plaintext
停止消息监控。
```
 
16. **exit**  - 退出程序

```plaintext
关闭程序并断开与 Telegram 的连接。
```

## 配置说明 

### 1. 关键词监控配置 
 
- **添加关键词** ： 
  - 使用 `addkeyword` 命令添加关键词。
 
  - 选择匹配类型：
    - 完全匹配

    - 关键词匹配

    - 正则表达式匹配

  - 输入需要监控的关键词或正则表达式。
 
  - 指定监听的对话 ID（可通过 `list` 命令获取）。
 
  - 选择需要监控的用户类型：
    - 用户 ID

    - 用户名

    - 昵称

    - 不指定（监听所有用户）

  - 选择是否启用自动转发和邮件通知功能。

  - 如果启用自动转发，需指定目标对话 ID。
 
- **修改关键词配置** ： 
  - 使用 `modifykeyword` 命令，根据提示修改关键词的配置。
 
- **移除关键词** ： 
  - 使用 `removekeyword` 命令，输入要移除的关键词。

### 2. 文件后缀名监控配置 
 
- **添加文件后缀名监控** ： 
  - 使用 `addext` 命令，输入需要监控的文件后缀名（如 `.pdf`）。

  - 指定监听的对话 ID。

  - 选择需要监控的用户。

  - 选择是否启用自动转发功能。
 
- **修改文件后缀名配置** ： 
  - 使用 `modifyext` 命令，根据提示修改文件后缀名的配置。
 
- **移除文件后缀名监控** ： 
  - 使用 `removeext` 命令，输入要移除的文件后缀名。

### 3. 定时消息配置 
 
- **添加定时消息** ： 
  - 使用 `schedule` 命令，输入目标对话 ID、消息内容、Cron 表达式等信息。
 
- **修改定时消息** ： 
  - 使用 `modifyschedule` 命令，根据提示修改定时消息的配置。
 
- **删除定时消息** ： 
  - 使用 `removeschedule` 命令，输入要删除的定时消息的 Job ID。

## 日志 
 
- 程序运行过程中，会将重要事件和错误信息记录到 `telegram_monitor.log` 文件中。
 
- 日志级别为 `INFO`，包含时间戳、日志级别和消息内容。

- 可以通过查看日志文件，了解程序的运行状态和调试信息。

## 注意事项 
 
- **Telegram 限制** ：请遵守 Telegram 的使用条款和限制，避免频繁发送消息或进行批量操作，防止账号被限制。
 
- **安全性** ：请妥善保管您的 `api_id`、`api_hash` 和 Telegram 登录会话文件，防止泄露。
 
- **邮件配置** ：如果需要使用邮件通知功能，请确保 SMTP 服务器信息和邮箱授权码正确配置。
 
- **Cron 表达式** ：定时消息的 Cron 表达式需符合标准格式，使用前建议测试表达式的正确性。

## 常见问题 
 
1. **程序无法连接到 Telegram** ：
  - 检查网络连接，确保可以访问 Telegram。
 
  - 确认 `api_id` 和 `api_hash` 是否正确。
 
2. **收不到邮件通知** ：
  - 检查邮件配置中的 SMTP 服务器信息和邮箱授权码。

  - 确认发件人和收件人邮箱是否正确。
 
3. **自动转发功能不起作用** ：
  - 确认已正确配置自动转发的目标对话 ID。

  - 检查日志文件，查看是否有错误信息。
 
4. **程序报错或异常退出** ：
  - 查看日志文件，查找错误原因。

  - 检查 Python 版本和依赖库是否符合要求。

## 贡献与支持 

欢迎对本项目提出意见和建议。如果您发现任何问题或有改进的想法，可以提交 issue 或 pull request。

## 许可证 

本项目采用 MIT 许可证。
