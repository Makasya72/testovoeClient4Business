OpenClaw — Telegram-бот
Результат выполнения тестового задания для Client4Business: OpenClaw развёрнут на Windows через WSL2 Ubuntu, подключён к AI-провайдеру и Telegram-боту @Test_Business4_bot.

Что включено
OpenClaw CLI установлен глобально в WSL2.

Node.js 24 установлен в WSL2.

Gateway установлен как пользовательский сервис systemd.

Telegram-канал настроен через токен BotFather.

Команды запуска

powershell
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway start"
wsl -d Ubuntu -- bash -lc ". ~/.openclaw/.env; openclaw gateway status"

Важные локальные пути

/root/.openclaw/openclaw.json
/root/.openclaw/.env
/root/.openclaw/workspace/SOUL.md
/root/.config/systemd/user/openclaw-gateway.service



Развернул OpenClaw на Windows через WSL2 Ubuntu, установил Node.js 24 и OpenClaw CLI через npm. Подключил Telegram-бота @Test_Business4_bot, настроил Gateway и проверил, что бот отвечает в личных сообщениях. Для AI использовал OpenAI API; 
