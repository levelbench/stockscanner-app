# Stock Scanner

**Windows desktop app for US equities swing trading: scanner, backtester, trade journal and AI assistant.** Free, closed source, bring your own market-data key.

*Инструмент для свинг-трейдинга акциями США: сканер, бэктестер, журнал сделок и AI-ассистент. Бесплатно. Русское описание — ниже.*

**[⬇ Download the latest release](../../releases/latest)**

---

## English

### What it does

- **Scanner** over ~8000 US stocks with configurable JSON profiles: base/consolidation, EMA pullbacks, adaptive MA signals, relative-strength rank, trend template, dollar-volume and earnings-date filters.
- **Backtester**: day-by-day simulation with no look-ahead, entry/stop/target mechanics, walk-forward (3 windows), portfolio simulation, grid-search parameter optimizer.
- **Trade journal** with per-setup attribution, equity curve, automatic order analysis down to minute bars, chart snapshots; **paper-trading** mode auto-creates virtual orders from scan signals.
- **Automation**: daily autopilot (update → scan → notification), price-level alerts.
- **AI assistant** (any OpenAI-compatible endpoint): setup scoring, entry/stop/target suggestions, morning briefing, per-ticker chat.
- **Charts**: daily/weekly/intraday (1m/5m/15m/1h), hand-drawn levels, virtual orders, EMA/ATR/Volume Profile; ThinkOrSwim export.
- Interface in English, Russian and Ukrainian.

### Install

1. Download `StockScanner-vX.Y.Z-win-x64.zip` from [Releases](../../releases/latest).
2. Unpack it anywhere — for example `C:\Apps\StockScanner`. **No installer, no .NET runtime needed**: the build is self-contained.
3. Run `StockScanner.App.exe`.

Windows SmartScreen will warn you that the publisher is unknown — the build is not code-signed. Click **More info → Run anyway**, or unblock the archive before unpacking (right-click → Properties → Unblock).

To update: download the new archive and unpack it over the old folder. Your data (journal, levels, watchlists, quotes database) lives outside the application folder and survives updates.

### First run

The app starts in demo mode with generated data, so you can look around before connecting anything. For real quotes you need your own data key — pick one provider in **⚙ Settings → 🔑 Data & API keys**:

| Provider | Cost | Notes |
|---|---|---|
| **Alpaca** | free key | full US history, IEX feed |
| **Schwab** | free for Schwab/ThinkOrSwim clients | OAuth, App Key from developer.schwab.com |
| **Massive** (ex-Polygon.io) | paid | fastest bulk path: the whole universe as one file per day |

Then: **Data → Update quotes**, pick scanners, press **▶ Scan**. Everything else is described in **❓ Help** inside the app.

An OpenAI-compatible key (OpenAI, OpenRouter, a local model) is optional and only needed for the AI features.

### What leaves your machine

Nothing goes to the author: there is no telemetry, no accounts, no servers of ours. The application talks only to the data provider whose key you entered, and — if you enabled AI — to the AI endpoint you configured. Quotes, your journal and your levels are stored locally in SQLite files.

### Disclaimer

Educational tool, not financial advice. Backtest and AI results do not guarantee future returns. Trading involves risk of loss; every decision is yours. Terms of use: see [LICENSE](LICENSE).

---

## Русский

### Что это

Десктоп-приложение (Windows) для свинг-трейдинга акциями США. Полный цикл: **скан → отбор → виртуальный ордер → журнал → бэктест**. Бесплатно, исходный код закрыт.

| Блок | Что умеет |
|---|---|
| **Сканер** | ~8000 акций, профили в JSON: базы, откаты к EMA21, AMA-сигналы, RS-ранг, трендовый шаблон, долларовый объём, фильтр «не входить перед отчётом» |
| **Бэктест** | посуточный прогон без заглядывания в будущее, walk-forward, портфельная симуляция, оптимизатор порогов |
| **Журнал** | атрибуция сделок к сканерам, кривая доходности, автоанализ ордеров вплоть до минутных баров, снимки графиков, фильтр по периоду, тикеру и статусу |
| **Paper-trading** | автосоздание виртуальных ордеров по сигналам профиля |
| **Автоматизация** | автопилот (данные → скан → уведомление), алерты у нарисованных уровней |
| **AI** | оценки сетапов, цели Entry/Stop/Target, утренний брифинг, чат по тикеру |
| **Графики** | день/неделя/интрадей (1m/5m/15m/1h), уровни, ордера, EMA/ATR-канал/Volume Profile, экспорт в ThinkOrSwim |

Интерфейс: русский, английский, украинский.

### Установка

1. Скачайте `StockScanner-vX.Y.Z-win-x64.zip` в разделе [Releases](../../releases/latest).
2. Распакуйте в любую папку, например `C:\Apps\StockScanner`. **Установщик и .NET не нужны** — сборка самодостаточная.
3. Запустите `StockScanner.App.exe`.

Windows SmartScreen скажет, что издатель неизвестен: сборка не подписана сертификатом. Нажмите **Подробнее → Выполнить в любом случае** или снимите блокировку с архива до распаковки (правой кнопкой → Свойства → Разблокировать).

Обновление: скачать новый архив и распаковать поверх старой папки. Данные (журнал, уровни, списки, база котировок) лежат вне папки приложения и обновление переживают.

### Первый запуск

Приложение стартует в демо-режиме на сгенерированных данных — можно осмотреться, ничего не подключая. Для настоящих котировок нужен свой ключ данных, источник выбирается в **⚙ Настройки → 🔑 Данные и ключи API**:

- **Alpaca** — бесплатный ключ, вся история США (фид IEX);
- **Schwab** — бесплатно клиентам Schwab/ThinkOrSwim, OAuth;
- **Massive** (бывш. Polygon.io) — платно, самый быстрый путь: вся вселенная одним файлом в день. Нужны две разные пары ключей: `API Key` и отдельные `S3 Access Key` + `Secret Key` для flat-files.

Дальше: **Данные → Обновить котировки**, отметить сканеры, **▶ Scan**. Остальное — в **❓ Справке** внутри приложения.

Ключ OpenAI-совместимого API нужен только для AI-функций и не обязателен.

### Что уходит с вашей машины

Автору — ничего: телеметрии нет, аккаунтов нет, наших серверов нет. Приложение обращается только к поставщику данных, чей ключ вы ввели, и — если включили AI — к указанному вами AI-endpoint. Котировки, журнал и уровни лежат локально в файлах SQLite.

### Отказ от ответственности

Инструмент технического анализа для образовательных целей. Не инвестиционная рекомендация. Результаты бэктестов и разборов модели не гарантируют будущую доходность. Торговля связана с риском потери капитала; решения вы принимаете сами. Условия использования — [LICENSE](LICENSE).
