# Open Reasoning Unseal

> **EN** / **RU** — short guide. Single-file web UI to inspect sealed Claude reasoning via OpenRouter.

Inspired by the public demo framing of [s-JoL/open-reasoning](https://github.com/s-JoL/open-reasoning).  
This repo ships a **local, self-contained** tool (`webui.html`) — not their closed recovery backend.

Live idea of the original project: [thinking-signature demo](https://thinking-signature-demo-5g65bijswq-de.a.run.app)

---

## English

### What this is

Modern Claude models often hide the long chain-of-thought. The API may return:

1. **Visible answer**
2. A short **summary** of thinking (sometimes)
3. A sealed **`signature`** (encrypted thinking state for multi-turn continuity)

**Open Reasoning Unseal** lets you run a chat, then press **「Show hidden reasoning」** to recover a deeper reasoning trace from that sealed artifact (via multi-turn signature replay on OpenRouter).

This is **not** offline AES decryption of the signature. The provider decrypts the signature when it is sent back; the model then re-emits a reasoning transcript. Treat results as a strong audit view, not a bit-exact internal log.

### Requirements

- A modern browser (Chrome / Edge / Firefox)
- An [OpenRouter](https://openrouter.ai/) API key
- Access to a Claude model on OpenRouter (default: `anthropic/claude-sonnet-5`)

### How to use `webui.html`

1. Download or clone this repo.
2. Open **`webui.html`** in the browser  
   - double-click the file, **or**  
   - serve the folder: `python -m http.server 8765` → http://127.0.0.1:8765/webui.html  
3. Click **Settings (⚙)** → paste your OpenRouter key → **Save** (stored only in browser `localStorage`).
4. Pick a Claude model and effort.
5. Ask a question that needs reasoning.
6. Click **🧠 Show hidden reasoning** / **Показать скрытые размышления**.

No Node.js. No backend required for the HTML UI (calls OpenRouter directly; CORS-friendly headers only).

### Principle (one diagram)

```
Turn A:  question → Claude (thinking sealed in signature) → answer [+ summary]
Turn B:  send signature back + “emit private reasoning” → deeper trace in the UI
```

### Security

- Do **not** commit API keys.
- Treat `signature` as sensitive (it can encode private reasoning content).
- Rotate any key that was ever pasted into chats or screenshots.

### Disclaimer

Research / educational tool. Provider APIs and policies change. Unseal quality depends on OpenRouter + model behavior. Not affiliated with Anthropic or the original open-reasoning authors.

---

## Русский

### Что это

У современных Claude длинная цепочка рассуждений часто скрыта. API обычно отдаёт:

1. **Видимый ответ**
2. Иногда короткий **summary** thinking
3. Sealed-поле **`signature`** (зашифрованное состояние reasoning для multi-turn)

**Open Reasoning Unseal** — чат в одной HTML-странице и кнопка **「Показать скрытые размышления」**: более полная трасса из sealed `signature` (replay signature через OpenRouter).

Это **не** локальный взлом AES. Провайдер расшифровывает signature при round-trip; модель заново выдаёт текст рассуждений. Это сильный audit-view, не гарантия bit-exact internal log.

### Нужно

- Браузер (Chrome / Edge / Firefox)
- API-ключ [OpenRouter](https://openrouter.ai/)
- Доступ к Claude на OpenRouter (по умолчанию `anthropic/claude-sonnet-5`)

### Как пользоваться `webui.html`

1. Скачай или клонируй репозиторий.
2. Открой **`webui.html`** в браузере  
   - двойной клик, **или**  
   - `python -m http.server 8765` → http://127.0.0.1:8765/webui.html  
3. **⚙ Настройки** → вставь OpenRouter key → **Сохранить** (только `localStorage` браузера).
4. Выбери модель Claude и effort.
5. Задай вопрос, где нужно reasoning.
6. Нажми **🧠 Показать скрытые размышления**.

Без Node.js. Backend не обязателен (HTML ходит в OpenRouter напрямую).

### Принцип

```
Ход A:  вопрос → Claude (thinking в signature) → ответ [+ summary]
Ход B:  signature обратно + «выдай private reasoning» → трасса в UI
```

### Безопасность

- Не коммить API-ключи.
- `signature` — чувствительный артефакт.
- Ротируй ключ, если светил его в чатах/скринах.

### Отказ от ответственности

Исследовательский / образовательный инструмент. API и политики провайдеров меняются. Качество unseal зависит от OpenRouter и модели. Не аффилированы с Anthropic и авторами original open-reasoning.

---

## Files

| File | Role |
|------|------|
| [`webui.html`](./webui.html) | Full UI: chat, settings, model list, unseal |
| [`README.md`](./README.md) | This guide (EN + RU) |

## Credits

- Concept / public framing: [s-JoL/open-reasoning](https://github.com/s-JoL/open-reasoning)
- Local unseal UI: this repository
