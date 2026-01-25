# bolt.new
# [![Bolt Open Source Codebase](./public/social_preview_index.jpg)](https://bolt.new)

> Welcome to the **Bolt** open-source codebase! This repo contains a simple example app using the core components from bolt.new to help you get started building **AI-powered software development tools** powered by StackBlitz’s **WebContainer API**.

### Why Build with Bolt + WebContainer API

By building with the Bolt + WebContainer API you can create browser-based applications that let users **prompt, run, edit, and deploy** full-stack web apps directly in the browser, without the need for virtual machines. With WebContainer API, you can build apps that give AI direct access and full control over a **Node.js server**, **filesystem**, **package manager** and **dev terminal** inside your users browser tab. This powerful combination allows you to create a new class of development tools that support all major JavaScript libraries and Node packages right out of the box, all without remote environments or local installs.

### What’s the Difference Between Bolt (This Repo) and [Bolt.new](https://bolt.new)?

- **Bolt.new**: This is the **commercial product** from StackBlitz—a hosted, browser-based AI development tool that enables users to prompt, run, edit, and deploy full-stack web applications directly in the browser. Built on top of the [Bolt open-source repo](https://github.com/stackblitz/bolt.new) and powered by the StackBlitz **WebContainer API**.

- **Bolt (This Repo)**: This open-source repository provides the core components used to make **Bolt.new**. This repo contains the UI interface for Bolt as well as the server components, built using [Remix Run](https://remix.run/). By leveraging this repo and StackBlitz’s **WebContainer API**, you can create your own AI-powered development tools and full-stack applications that run entirely in the browser.

# Get Started Building with Bolt

Bolt combines the capabilities of AI with sandboxed development environments to create a collaborative experience where code can be developed by the assistant and the programmer together. Bolt combines [WebContainer API](https://webcontainers.io/api) with [Claude Sonnet 3.5](https://www.anthropic.com/news/claude-3-5-sonnet) using [Remix](https://remix.run/) and the [AI SDK](https://sdk.vercel.ai/).

### WebContainer API

Bolt uses [WebContainers](https://webcontainers.io/) to run generated code in the browser. WebContainers provide Bolt with a full-stack sandbox environment using [WebContainer API](https://webcontainers.io/api). WebContainers run full-stack applications directly in the browser without the cost and security concerns of cloud hosted AI agents. WebContainers are interactive and editable, and enables Bolt's AI to run code and understand any changes from the user.

The [WebContainer API](https://webcontainers.io) is free for personal and open source usage. If you're building an application for commercial usage, you can learn more about our [WebContainer API commercial usage pricing here](https://stackblitz.com/pricing#webcontainer-api).

### Remix App

Bolt is built with [Remix](https://remix.run/) and
deployed using [CloudFlare Pages](https://pages.cloudflare.com/) and
[CloudFlare Workers](https://workers.cloudflare.com/).

### AI SDK Integration

Bolt uses the [AI SDK](https://github.com/vercel/ai) to integrate with AI
models. At this time, Bolt supports using Anthropic's Claude Sonnet 3.5.
You can get an API key from the [Anthropic API Console](https://console.anthropic.com/) to use with Bolt.
Take a look at how [Bolt uses the AI SDK](https://github.com/stackblitz/bolt.new/tree/main/app/lib/.server/llm)

## Prerequisites

Before you begin, ensure you have the following installed:

- Node.js (v20.15.1)
- pnpm (v9.4.0)

## Setup

1. Clone the repository (if you haven't already):

```bash
git clone https://github.com/stackblitz/bolt.new.git
```

2. Install dependencies:

```bash
pnpm install
```

3. Create a `.env.local` file in the root directory and add your Anthropic API key:

```
ANTHROPIC_API_KEY=XXX
```

Optionally, you can set the debug level:

```
VITE_LOG_LEVEL=debug
```

**Important**: Never commit your `.env.local` file to version control. It's already included in .gitignore.

## Available Scripts

- `pnpm run dev`: Starts the development server.
- `pnpm run build`: Builds the project.
- `pnpm run start`: Runs the built application locally using Wrangler Pages. This script uses `bindings.sh` to set up necessary bindings so you don't have to duplicate environment variables.
- `pnpm run preview`: Builds the project and then starts it locally, useful for testing the production build. Note, HTTP streaming currently doesn't work as expected with `wrangler pages dev`.
- `pnpm test`: Runs the test suite using Vitest.
- `pnpm run typecheck`: Runs TypeScript type checking.
- `pnpm run typegen`: Generates TypeScript types using Wrangler.
- `pnpm run deploy`: Builds the project and deploys it to Cloudflare Pages.

## Development

To start the development server:

```bash
pnpm run dev
```

This will start the Remix Vite development server.

## Testing

Run the test suite with:

```bash
pnpm test
```

## Deployment

To deploy the application to Cloudflare Pages:

```bash
pnpm run deploy
```

Make sure you have the necessary permissions and Wrangler is correctly configured for your Cloudflare account.
# dependabot/npm_and_yarn/npm_and_yarn-226995c71a
# Инструкция по удалению монетизации из Bolt.new
📋 Предварительные требования
Перед началом убедитесь, что у вас установлено:
Git (проверьте: git --version)
Node.js версии 18+ (проверьте: node --version)
npm или pnpm (проверьте: npm --version)
Опционально: jq для автоматической обработки JSON (проверьте: jq --version)
🚀 Шаг 1: Клонирование репозитория
# Клонируем оригинальный репозиторий
git clone https://github.com/stackblitz/bolt.new.git
cd bolt.new

# Или если у вас уже есть форк:
git clone https://github.com/YOUR_USERNAME/bolt.new.git
cd bolt.new
📥 Шаг 2: Подготовка скрипта
Сохраните скрипт из артефакта в файл remove-monetization.sh в корневой директории проекта:
# Создайте файл и скопируйте в него содержимое скрипта
nano remove-monetization.sh

# Или используйте любой текстовый редактор
Сделайте скрипт исполняемым:
chmod +x remove-monetization.sh
▶️ Шаг 3: Запуск скрипта
./remove-monetization.sh
Что делает скрипт:
Создаёт резервную копию - создаётся git ветка backup-before-demonetization
Удаляет файлы - находит и удаляет файлы с монетизацией по паттернам
Комментирует импорты - автоматически комментирует связанные импорты
Обновляет package.json - удаляет зависимости Stripe (если установлен jq)
Создаёт конфиги - генерирует config.demonetized.json и .env.example
Коммитит изменения - сохраняет всё в новой ветке demonetization-removed
⚙️ Шаг 4: Настройка окружения
Создайте файл .env на основе .env.example:
cp .env.example .env
Отредактируйте .env и добавьте ваши API ключи:
# Откройте в редакторе
nano .env
Заполните необходимые ключи:
ANTHROPIC_API_KEY=sk-ant-ваш-ключ-здесь
OPENAI_API_KEY=sk-ваш-ключ-здесь
GROQ_API_KEY=gsk_ваш-ключ-здесь

ENABLE_BILLING=false
ENABLE_SUBSCRIPTIONS=false
ENABLE_USAGE_LIMITS=false
Где получить API ключи:
Anthropic Claude: https://console.anthropic.com/
OpenAI: https://platform.openai.com/api-keys
Groq: https://console.groq.com/
📦 Шаг 5: Установка зависимостей
# Если используете npm:
npm install

# Если используете pnpm (рекомендуется):
pnpm install

# Если используете yarn:
yarn install
🔍 Шаг 6: Проверка изменений
Посмотрите, что изменилось:
# Просмотр всех изменений
git diff backup-before-demonetization

# Просмотр удалённых файлов
git diff backup-before-demonetization --diff-filter=D --name-only

# Список изменённых файлов
git diff backup-before-demonetization --name-only
🛠️ Шаг 7: Ручная доработка (если необходимо)
Скрипт автоматизирует большую часть работы, но могут остаться упоминания монетизации в:
1. Компонентах UI
Проверьте файлы в src/components/ на наличие:
Баннеров с призывами к оплате
Модальных окон подписки
Индикаторов лимитов
2. Роутах и middleware
Проверьте src/routes/ или app/ на:
Маршруты /billing, /subscribe, /pricing
Проверки подписки в middleware
Редиректы на страницы оплаты
3. Конфигурационных файлах
Откройте и проверьте:
# Поиск упоминаний монетизации
grep -r "subscription" src/ --include="*.ts" --include="*.tsx"
grep -r "billing" src/ --include="*.ts" --include="*.tsx"
grep -r "paywall" src/ --include="*.ts" --include="*.tsx"
Закомментируйте или удалите найденные блоки кода.
🎯 Шаг 8: Запуск приложения
# Режим разработки
npm run dev

# Или с pnpm
pnpm dev
Откройте браузер и перейдите на http://localhost:3000 (или другой порт, указанный в консоли).
✅ Шаг 9: Тестирование
Проверьте основной функционал:
Создание проекта - попробуйте создать новый проект
AI запросы - проверьте работу AI ассистента
Редактирование кода - убедитесь, что редактор работает
Нет блокировок - убедитесь, что нет paywall или лимитов
🔄 Откат изменений (если нужно)
Если что-то пошло не так, вернитесь к исходной версии:
# Вернуться к резервной копии
git checkout backup-before-demonetization

# Или удалить все изменения
git reset --hard backup-before-demonetization
🐛 Решение проблем
Ошибка: "Module not found"
# Переустановите зависимости
rm -rf node_modules package-lock.json
npm install
Ошибка: "API key not found"
Проверьте, что .env файл:
Находится в корневой директории
Содержит все необходимые ключи
Имена переменных написаны правильно
Ошибки TypeScript
# Проверьте типы
npm run type-check

# Или пропустите проверку типов временно
npm run dev -- --no-type-check
Скрипт не запускается
# Проверьте права доступа
ls -la remove-monetization.sh

# Убедитесь, что файл исполняемый
chmod +x remove-monetization.sh

# Запустите напрямую через bash
bash remove-monetization.sh
📚 Дополнительные настройки
Отключение аналитики (опционально)
Добавьте в .env:
DISABLE_ANALYTICS=true
DISABLE_TELEMETRY=true
Увеличение лимитов токенов
В config.demonetized.json уже установлено -1 (безлимит), но вы можете настроить:
{
  "limits": {
    "maxTokens": 100000,
    "maxRequestsPerHour": 1000
  }
}
🎉 Готово!
Теперь у вас есть полностью рабочая версия Bolt.new без монетизации. Вы можете:
Использовать её локально без ограничений
Развернуть на своём сервере
Дорабатывать под свои нужды
Делиться с командой
⚠️ Важные замечания
Соблюдайте лицензию - убедитесь, что ваше использование соответствует лицензии проекта
API ключи - храните их в безопасности, не коммитьте в git
Обновления - при обновлении upstream репозитория может потребоваться повторный запуск скрипта
Поддержка - это самостоятельная сборка, официальная поддержка может быть недоступна
📞 Помощь
Если возникли проблемы:
Проверьте логи в консоли разработчика
Изучите Issues в оригинальном репозитории Bolt.new
Проверьте документацию API провайдеров (Anthropic, OpenAI)
