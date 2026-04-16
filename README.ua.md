# Language Card — Шаблон для Anki

**Language / Мова / Язык:** [🇬🇧 English](README.en.md) &nbsp;·&nbsp; 🇺🇦 Українська &nbsp;·&nbsp; [🇷🇺 Русский](README.ru.md)

---

Двомовний тип записів Anki для вивчення лексики: слів, словосполучень і фраз. Один запис генерує дві картки — **Target → Native** (рецептивна) і **Native → Target** (продуктивна). Працює з будь-якою мовною парою.

![Preview](preview/screenshot.png)

## Швидкий старт

Завантаж [`language-card-sample.apkg`](language-card-sample.apkg) і імпортуй у Anki (**File → Import**). Тип записів з усіма полями і шаблонами, а також тестова картка, додадуться автоматично.

Для ручного налаштування з вихідного коду — дивись розділ [Встановлення](#встановлення) нижче.

## Можливості

- Теплий, дружній дизайн — працює на iPhone (AnkiMobile), iPad і десктопному Anki
- Два напрямки карток з одного запису
- Cloze-розкриття в прикладі: напиши `[слово]` — на картці з'явиться помаранчевий блок
- Опціональні поля: зображення, аудіо, транскрипція, нотатки — зникають коли порожні
- Підтримка нічного режиму

## Поля

| Поле | Обов'язкове | Опис |
|------|-------------|------|
| `Word` | ✓ | Слово, словосполучення або фраза мови, яку вивчаєш |
| `Translation` | ✓ | Переклад рідною мовою |
| `PartOfSpeech` | ✓ | напр. `noun`, `verb`, `adjective`, `phrase`, `collocation` |
| `Transcription` | — | IPA транскрипція, напр. `æmˈbɪv.ə.lənt` |
| `ExampleTarget` | ✓ | Приклад речення. Оберни ключове слово у `[дужки]` для cloze |
| `ExampleNative` | ✓ | Переклад прикладу рідною мовою |
| `Audio` | — | Аудіофайл, напр. `[sound:word.mp3]` |
| `Image` | — | Зображення додане через медіа Anki |
| `Notes` | — | Нотатки: регістр, типові словосполучення, пастки |

### Синтаксис cloze

У полі `ExampleTarget` оберни ключове слово або фразу у квадратні дужки:

```
She felt [ambivalent] about the decision.
```

На **лицьовій** стороні Target → Native слово буде показане як помаранчевий блок. Натисни — і слово відкриється. На **зворотній** стороні воно виділено жирним.

## Встановлення

### 1. Створити новий тип записів

Відкрий Anki → **Tools → Manage Note Types → Add**

Вибери **"Add: Basic"** як основу. Назви його `Language Card`.

### 2. Додати поля

Натисни **Fields**. Перейменуй стандартні поля та додай решту в точному порядку:

1. `Word`
2. `Translation`
3. `PartOfSpeech`
4. `Transcription`
5. `ExampleTarget`
6. `ExampleNative`
7. `Audio`
8. `Image`
9. `Notes`

Натисни **Save**.

### 3. Вставити CSS

Натисни **Cards → Styling**. Видали весь вміст і встав вміст файлу [`src/style.css`](src/style.css).

### 4. Налаштувати Card 1 — Target → Native

Переконайся, що вибрано **Card 1**.

- **Front Template** — видали все, встав [`src/front-target-native.html`](src/front-target-native.html)
- **Back Template** — видали все, встав [`src/back-target-native.html`](src/back-target-native.html)
- Перейменуй: **Options → Rename Card Type** → `Target → Native`

### 5. Додати Card 2 — Native → Target

Натисни **Add Card Type**.

- **Front Template** — видали все, встав [`src/front-native-target.html`](src/front-native-target.html)
- **Back Template** — видали все, встав [`src/back-native-target.html`](src/back-native-target.html)
- Перейменуй: **Options → Rename Card Type** → `Native → Target`

Натисни **Save / Close**.

### 6. Перевірити на тестовому записі

Додай новий запис з типом `Language Card`:

| Поле | Значення |
|------|----------|
| Word | `ambivalent` |
| Translation | `двоїстий` |
| PartOfSpeech | `adjective` |
| Transcription | `æmˈbɪv.ə.lənt` |
| ExampleTarget | `She felt [ambivalent] about the decision.` |
| ExampleNative | `Вона відчувала двоїсті почуття щодо цього рішення.` |
| Notes | `often used with "about" · formal register` |

Переглянь обидві картки. Натисни на помаранчевий блок — слово має відкритися.

## Структура проекту

```
anki-card-template/
├── src/
│   ├── style.css                  # Спільний CSS → вставити в розділ Styling
│   ├── front-target-native.html   # Шаблон лицьової сторони Card 1
│   ├── back-target-native.html    # Шаблон зворотної сторони Card 1
│   ├── front-native-target.html   # Шаблон лицьової сторони Card 2
│   └── back-native-target.html    # Шаблон зворотної сторони Card 2
└── preview/
    └── index.html                 # Візуальний перегляд — відкрий у браузері
```
