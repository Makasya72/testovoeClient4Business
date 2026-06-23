# OpenClaw Telegram bot setup

Test task result for Client4Business: OpenClaw was deployed on Windows through WSL2 Ubuntu, connected to an AI provider and Telegram bot `@Test_Business4_bot`.

## What is included

- OpenClaw CLI installed globally in WSL2.
- Node.js 24 installed in WSL2.
- Gateway installed as a systemd user service.
- Telegram channel configured through BotFather token.
- AI provider configured through environment-backed secrets.
- Custom assistant persona in `SOUL.md`.

Secrets are not committed. Runtime tokens live only in `~/.openclaw/.env` on the local machine.

## Current verified status

- Gateway service starts and listens on `127.0.0.1:18789`.
- Telegram Bot API token is valid for `@Test_Business4_bot`.
- Telegram long polling is used, so no webhook/ngrok is required.
- The bot answered in a private Telegram chat during verification.

Note: the submitted OpenAI API key later returned `insufficient_quota`, so new AI responses may show a quota error until billing/quota is fixed or the key is replaced.

## Start commands

Run from Windows PowerShell:

```powershell
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway start"
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway status"
```

Optional CLI smoke test:

```powershell
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw agent --agent main --session-key smoke --message 'Привет'"
```

## Important local paths

```text
/root/.openclaw/openclaw.json
/root/.openclaw/.env
/root/.openclaw/workspace/SOUL.md
/root/.config/systemd/user/openclaw-gateway.service
```

## Required environment variables

Create or update `/root/.openclaw/.env` in WSL:

```bash
OPENAI_API_KEY='replace-me'
TELEGRAM_BOT_TOKEN='replace-me'
TELEGRAM_BOT_USERNAME='@Test_Business4_bot'
OPENCLAW_GATEWAY_TOKEN='replace-me'
```

`GEMINI_API_KEY` was tested first, but Gemini API returned a regional restriction error in this environment.

## Screencast checklist

1. Show `openclaw gateway status` with the Gateway running.
2. Show Telegram chat with `@Test_Business4_bot`.
3. Send a message to the bot and show the received reply or the provider quota error.
4. Briefly explain that OpenClaw was installed in WSL2, Telegram was configured through BotFather, and AI was connected through OpenAI API.
5. Mention the real difficulty: Gemini was blocked by region, then OpenAI quota became the limiting factor.

## Submission text

Развернул OpenClaw на Windows через WSL2 Ubuntu, установил Node.js 24 и OpenClaw CLI через npm. Подключил Telegram-бота `@Test_Business4_bot`, настроил Gateway и проверил, что бот отвечает в личных сообщениях. Для AI использовал OpenAI API; сначала пробовал Gemini, но он оказался недоступен по региону. Основная трудность была в лимитах/квотах провайдера и настройке фонового Gateway-сервиса. Время выполнения заняло примерно несколько часов с отладкой.
