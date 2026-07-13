# Open Reasoning Unseal

> **EN** / **RU**

Inspired by [s-JoL/open-reasoning](https://github.com/s-JoL/open-reasoning).  
This repo is a **local single-file UI** (`webui.html`) — not their closed backend.

---

## English

### Idea

Claude often hides the long chain-of-thought. The API may return:

1. **Answer**
2. Optional short **summary** of thinking
3. Sealed **`signature`** (encrypted thinking state)

Open **`webui.html`**, chat via OpenRouter, then press **Show hidden reasoning** — a deeper trace recovered by replaying that signature (not offline crypto; the provider decrypts on round-trip, the model re-emits the reasoning text).

### How to use

1. Open **`webui.html`** in the browser (double-click).
2. **Settings** → paste [OpenRouter](https://openrouter.ai/) API key → Save (browser `localStorage` only).
3. Pick a Claude model (default `anthropic/claude-sonnet-5`) and effort.
4. Ask a question → **🧠 Show hidden reasoning**.

No install. No Node.js. No backend.

### Principle

```
Turn A: question → Claude → answer + sealed signature
Turn B: send signature back → UI shows recovered reasoning
```

---

## Русский

### Суть

Claude часто прячет длинное reasoning. API может отдать:

1. **Ответ**
2. Короткий **summary** thinking (не всегда)
3. Sealed **`signature`** (зашифрованное состояние reasoning)

Открой **`webui.html`**, общайся через OpenRouter, нажми **Показать скрытые размышления** — более полная трасса из signature (не локальный взлом AES: провайдер расшифровывает при round-trip, модель выдаёт текст).

### Как пользоваться

1. Открой **`webui.html`** в браузере (двойной клик).
2. **Настройки** → ключ [OpenRouter](https://openrouter.ai/) → Сохранить (только `localStorage`).
3. Модель Claude (по умолчанию `anthropic/claude-sonnet-5`) и effort.
4. Вопрос → **🧠 Показать скрытые размышления**.

Без установки. Без Node.js. Без сервера.

### Принцип

```
Ход A: вопрос → Claude → ответ + sealed signature
Ход B: signature обратно → в UI трасса рассуждений
```

---

## Files

| File | Role |
|------|------|
| [`webui.html`](./webui.html) | Full UI |
| [`README.md`](./README.md) | EN + RU |

## Credits

- Framing: [s-JoL/open-reasoning](https://github.com/s-JoL/open-reasoning)
- Local unseal UI: this repo
