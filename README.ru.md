# Language Card — Шаблон для Anki

**Language / Мова / Язык:** [🇬🇧 English](README.en.md) &nbsp;·&nbsp; [🇺🇦 Українська](README.ua.md) &nbsp;·&nbsp; 🇷🇺 Русский

---

Двуязычный тип записей Anki для изучения лексики: слов, коллокаций и фраз. Одна запись генерирует две карточки — **Target → Native** (рецептивная) и **Native → Target** (продуктивная). Работает с любой языковой парой.

![Preview](preview/screenshot.png)

## Быстрый старт

Скачай [`language-card-sample.apkg`](language-card-sample.apkg) и импортируй в Anki (**File → Import**). Тип записей со всеми полями и шаблонами, а также тестовая карточка, добавятся автоматически.

Для ручной настройки из исходников — см. раздел [Установка](#установка) ниже.

## Возможности

- Тёплый, дружелюбный дизайн — работает на iPhone (AnkiMobile), iPad и десктопном Anki
- Два направления карточек из одной записи
- Cloze-раскрытие в примере: напиши `[слово]` — на карточке появится оранжевый блок
- Опциональные поля: картинка, аудио, транскрипция, заметки — исчезают когда пустые
- Поддержка ночного режима

## Поля

| Поле | Обязательное | Описание |
|------|-------------|----------|
| `Word` | ✓ | Слово, коллокация или фраза изучаемого языка |
| `Translation` | ✓ | Перевод на родной язык |
| `PartOfSpeech` | ✓ | напр. `noun`, `verb`, `adjective`, `phrase`, `collocation` |
| `Transcription` | — | IPA транскрипция, напр. `æmˈbɪv.ə.lənt` |
| `ExampleTarget` | ✓ | Пример предложения. Оберни ключевое слово в `[скобки]` для cloze |
| `ExampleNative` | ✓ | Перевод примера на родной язык |
| `Audio` | — | Аудиофайл, напр. `[sound:word.mp3]` |
| `Image` | — | Картинка добавленная через медиа Anki |
| `Notes` | — | Заметки: регистр, типичные коллокации, частые ошибки |

### Синтаксис cloze

В поле `ExampleTarget` оберни ключевое слово или фразу в квадратные скобки:

```
She felt [ambivalent] about the decision.
```

На **лицевой** стороне Target → Native слово будет показано как оранжевый блок. Нажми — и слово откроется. На **обратной** стороне оно выделено жирным.

## Установка

### 1. Создать новый тип записей

Открой Anki → **Tools → Manage Note Types → Add**

Выбери **"Add: Basic"** как основу. Назови его `Language Card`.

### 2. Добавить поля

Нажми **Fields**. Переименуй стандартные поля и добавь остальные в точном порядке:

1. `Word`
2. `Translation`
3. `PartOfSpeech`
4. `Transcription`
5. `ExampleTarget`
6. `ExampleNative`
7. `Audio`
8. `Image`
9. `Notes`

Нажми **Save**.

### 3. Вставить CSS

Нажми **Cards → Styling**. Удали весь контент и вставь содержимое файла [`src/style.css`](src/style.css).

### 4. Настроить Card 1 — Target → Native

Убедись, что выбрана **Card 1**.

- **Front Template** — удали всё, вставь [`src/front-target-native.html`](src/front-target-native.html)
- **Back Template** — удали всё, вставь [`src/back-target-native.html`](src/back-target-native.html)
- Переименуй: **Options → Rename Card Type** → `Target → Native`

### 5. Добавить Card 2 — Native → Target

Нажми **Add Card Type**.

- **Front Template** — удали всё, вставь [`src/front-native-target.html`](src/front-native-target.html)
- **Back Template** — удали всё, вставь [`src/back-native-target.html`](src/back-native-target.html)
- Переименуй: **Options → Rename Card Type** → `Native → Target`

Нажми **Save / Close**.

### 6. Проверить на тестовой записи

Добавь новую запись с типом `Language Card`:

| Поле | Значение |
|------|----------|
| Word | `ambivalent` |
| Translation | `двойственный` |
| PartOfSpeech | `adjective` |
| Transcription | `æmˈbɪv.ə.lənt` |
| ExampleTarget | `She felt [ambivalent] about the decision.` |
| ExampleNative | `Она испытывала двойственные чувства по поводу этого решения.` |
| Notes | `often used with "about" · formal register` |

Просмотри обе карточки. Нажми на оранжевый блок — слово должно раскрыться.

## Структура проекта

```
anki-card-template/
├── src/
│   ├── style.css                  # Общий CSS → вставить в раздел Styling
│   ├── front-target-native.html   # Шаблон лицевой стороны Card 1
│   ├── back-target-native.html    # Шаблон обратной стороны Card 1
│   ├── front-native-target.html   # Шаблон лицевой стороны Card 2
│   └── back-native-target.html    # Шаблон обратной стороны Card 2
└── preview/
    └── index.html                 # Визуальный предпросмотр — открой в браузере
```
