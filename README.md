# Open Reasoning Unseal

**Live:** [myslithell.github.io/open-reasoning-unseal](https://myslithell.github.io/open-reasoning-unseal/)

## Idea

Claude often hides the long chain-of-thought. The API may return:

1. **Answer**
2. Optional short **summary** of thinking
3. Sealed **`signature`** (encrypted thinking state)

Open **`webui.html`**, chat via OpenRouter, then press **Show hidden reasoning** — a deeper trace recovered by replaying that signature (not offline crypto; the provider decrypts on round-trip, the model re-emits the reasoning text).

**How the “unseal” works:** the first response keeps full thinking inside `signature` and does not show it. The button sends that signature back in a second request; the API restores the private reasoning into the model’s context, and a follow-up prompt asks the model to write it out as text. Without a valid signature there is nothing sealed to recover — it is not just “think again.”

## How to use

1. Open **`webui.html`** in the browser (double-click).
2. **Settings** → paste [OpenRouter](https://openrouter.ai/) API key → Save (browser `localStorage` only).
3. Pick a Claude model (default `anthropic/claude-sonnet-5`) and effort.
4. Ask a question → **🧠 Show hidden reasoning**.

No install. No Node.js. No backend.

## Principle

```
Turn A: question → Claude → answer + sealed signature
Turn B: send signature back → UI shows recovered reasoning
```

---

## Суть

Claude часто прячет длинное reasoning. API может отдать:

1. **Ответ**
2. Короткий **summary** thinking (не всегда)
3. Sealed **`signature`** (зашифрованное состояние reasoning)

Открой **`webui.html`**, общайся через OpenRouter, нажми **Показать скрытые размышления** — более полная трасса из signature (не локальный взлом AES: провайдер расшифровывает при round-trip, модель выдаёт текст).

**Как устроен unseal:** в первом ответе полное thinking спрятано в `signature` и тебе не показывается. Кнопка отправляет эту signature вторым запросом: API снова подставляет private reasoning в контекст модели, а follow-up prompt просит выдать его текстом. Без валидной signature «разпечатывать» нечего — это не просто «подумай ещё раз».

## Как пользоваться

1. Открой **`webui.html`** в браузере (двойной клик).
2. **Настройки** → ключ [OpenRouter](https://openrouter.ai/) → Сохранить (только `localStorage`).
3. Модель Claude (по умолчанию `anthropic/claude-sonnet-5`) и effort.
4. Вопрос → **🧠 Показать скрытые размышления**.

Без установки. Без Node.js. Без сервера.

## Принцип

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

## More from me

Want more AI tools, edge tricks, and research-grade finds? Join the Telegram: [t.me channel](https://t.me/+gxt0pJ7jMxxhODZi)

Если хочешь больше интересных штук про ИИ — заходи в [Telegram-канал](https://t.me/+gxt0pJ7jMxxhODZi).

## Credits

Inspired by [s-JoL/open-reasoning](https://github.com/s-JoL/open-reasoning); built this because their recovery is closed.
