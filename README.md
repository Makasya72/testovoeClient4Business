# OpenClaw — Telegram-бот

> Результат выполнения тестового задания для **Client4Business**: OpenClaw развёрнут на Windows через WSL2 Ubuntu, подключён к AI-провайдеру и Telegram-боту [@Test_Business4_bot](https://t.me/Test_Business4_bot).

---

## Что включено

| Компонент | Статус |
|---|---|
| OpenClaw CLI | Установлен глобально в WSL2 |
| Node.js 24 | Установлен в WSL2 |
| Gateway | Установлен как пользовательский сервис systemd |
| Telegram-канал | Настроен через токен BotFather |
| AI-провайдер | OpenAI API |

---

## Команды запуска

```powershell
# Запуск Gateway
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway start"

# Проверка статуса Gateway
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway status"
```

---

## Важные локальные пути

| Файл | Назначение |
|---|---|
| `/root/.openclaw/openclaw.json` | Конфигурация OpenClaw |
| `/root/.openclaw/.env` | Переменные окружения (токены, ключи) |
| `/root/.openclaw/workspace/SOUL.md` | Файл промпта / «души» бота |
| `/root/.config/systemd/user/openclaw-gateway.service` | Systemd-сервис для автозапуска Gateway |

---

## Установка и настройка

### 1. Подготовка WSL2

```powershell
wsl --install -d Ubuntu
```

### 2. Установка Node.js 24

```bash
curl -fsSL https://deb.nodesource.com/setup_24.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### 3. Установка OpenClaw CLI

```bash
npm install -g openclaw
```

### 4. Настройка окружения

Создайте файл `/root/.openclaw/.env` с переменными окружения:

```env
OPENAI_API_KEY=<ваш_ключ>
TELEGRAM_BOT_TOKEN=<токен_от_BotFather>
```

### 5. Запуск и проверка

```powershell
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway start"
```

После запуска бот [@Test_Business4_bot](https://t.me/Test_Business4_bot) готов отвечать в личных сообщениях Telegram.
