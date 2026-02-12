# Посібники для вивчення APR

**Automated Plan Reviser Pro (APR)** — це інструмент для автоматизації ітеративного вдосконалення специфікацій через AI. Цей посібник допоможе вам опанувати кращі практики роботи з APR.

## 📋 Зміст

1. [🚀 Швидкий старт: ваш перший робочий процес](#швидкий-старт-ваш-перший-робочий-процес)
2. [🎯 Кращі практики планування специфікацій](#кращі-практики-планування-специфікацій)
3. [🔄 Оптимальні стратегії ітерацій](#оптимальні-стратегії-ітерацій)
4. [📊 Розуміння конвергенції та аналітики](#розуміння-конвергенції-та-аналітики)
5. [🤖 Автоматизація через Robot Mode](#автоматизація-через-robot-mode)
6. [🛠️ Налаштування складних workflow](#налаштування-складних-workflow)
7. [🚨 Вирішення проблем та діагностика](#вирішення-проблем-та-діагностика)
8. [📚 Додаткові ресурси](#додаткові-ресурси)

---

## 🚀 Швидкий старт: ваш перший робочий процес

Цей розділ проведе вас крок за кроком від встановлення до отримання першого результату від GPT Pro.

### Крок 1: Встановлення та підготовка

```bash
# 1. Встановіть APR
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/automated_plan_reviser_pro/main/install.sh?$(date +%s)" | bash

# 2. Встановіть Oracle (обов'язково)
npm install -g @steipete/oracle

# 3. Перевірте, що все працює
apr --version
oracle --version
```

> **💡 Порада:** Детальні інструкції встановлення дивіться в [Quickstart розділі README](README.md#-quickstart).

### Крок 2: Підготовка вашого проекту

Перед початком роботи з APR переконайтеся, що у вас є:

```bash
# Перейдіть до директорії вашого проекту
cd /path/to/your/project

# Перевірте наявність ключових файлів
ls README.md       # Основна документація проекту
ls SPEC.md         # Ваша специфікація (або інший файл)
ls src/            # Код реалізації (опціонально)
```

**Мінімальні вимоги для початку:**

- `README.md` — опис проекту
- Файл специфікації (може називатися `SPEC.md`, `DESIGN.md`, `PROTOCOL.md` тощо)

### Крок 3: Перший запуск setup

```bash
# Запустіть інтерактивний майстер налаштувань
apr setup
```

**Що відбувається під час setup:**

1. **Назва workflow** — дайте зрозумілу назву (наприклад, `auth-protocol` або `payment-system`)
2. **Вибір файлів:**
   - **README file** — виберіть основний опис проекту
   - **Spec file** — файл зі специфікацією для ревізії
   - **Implementation files** — код реалізації (можна додати пізніше)
3. **Збереження конфігурації** — створюється `.apr/workflows/[назва].yaml`

> **🔍 Детальніше:** Дивіться [Interactive Setup в README](README.md#-interactive-setup).

### Крок 4: Ваш перший раунд ревізії

```bash
# Перший раунд потребує ручного входу в ChatGPT
apr run 1 --login --wait

# Після входу в браузер:
# 1. Увійдіть в ChatGPT
# 2. APR автоматично відправить ваші документи
# 3. Дочекайтеся завершення (10-60 хвилин)
```

**Що відбувається:**

- APR об'єднує ваші документи в єдиний промпт
- Відкривається браузер з ChatGPT (потрібен лише перший раз)
- GPT Pro аналізує специфікацію та дає рекомендації
- Результат зберігається в `.apr/rounds/[workflow]/round_1.md`

### Крок 5: Перегляд результатів

```bash
# Переглянути результат першого раунду
apr show 1

# Або відкрити файл напряму
cat .apr/rounds/default/round_1.md
```

**🎉 Вітаємо!** Ви щойно завершили свій перший цикл ревізії з APR.

---

## 🎯 Кращі практики планування специфікацій

Ефективність APR залежить від якості вхідних документів. Ось перевірені підходи:

### Структура ідеальної специфікації

```markdown
# Protocol/System Name

## Огляд

- Що робить система
- Основні цілі та вимоги
- Ключові учасники

## Архітектура

- Компоненти системи
- Взаємодії між компонентами
- Діаграми (ASCII або посилання)

## Детальна специфікація

- API endpoints
- Структури даних
- Алгоритми та процедури

## Безпека

- Загрози та ризики
- Міри захисту
- Аутентифікація та авторизація

## Обмеження та припущення

- Технічні обмеження
- Припущення про середовище
- Відомі проблеми
```

### Підготовка документів для ревізії

**README.md повинен містити:**

```markdown
# Проект: [Назва]

## TL;DR

Короткий опис що робить проект

## Мотивація

Чому цей проект потрібен

## Архітектура

Загальна структура системи

## Статус розробки

Що готово, що в процесі, що планується
```

**Файл специфікації (SPEC.md):**

- Деталізований технічний дизайн
- Конкретні алгоритми та протоколи
- Приклади використання
- Edge cases та обробка помилок

### Кращі практики контенту

**✅ Рекомендується:**

- Конкретність замість абстракції
- Приклади та use cases
- Явні обмеження та припущення
- Секції безпеки та обробки помилок

**❌ Уникайте:**

- Розпливчатих формулювань ("система повинна бути швидкою")
- Відсутності контексту
- Занадто великих блоків тексту без структури
- Застарілої інформації

---

## 🔄 Оптимальні стратегії ітерацій

APR працює як алгоритм оптимізації — кожен раунд поліпшує специфікацію. Ось як отримати максимальну користь:

### Типовий цикл конвергенції

```
Раунди 1-3:   🔧 Архітектурні виправлення, виявлення проблем безпеки
Раунди 4-7:   ⚡ Покращення архітектури, оптимізація інтерфейсів
Раунди 8-12:  🎯 Нюансовані оптимізації, обробка граничних випадків
Раунди 13+:   ✨ Полірування абстракцій, стабілізація дизайну
```

> **📖 Детальніше:** [The Convergence Pattern в README](README.md#the-convergence-pattern).

### Стратегія включення коду реалізації

**Кожні 3-4 раунди включайте реалізацію:**

```bash
# Раунди без коду (фокус на дизайні)
apr run 1
apr run 2
apr run 3

# Раунд з кодом реалізації
apr run 4 --include-impl

# Знову без коду
apr run 5
apr run 6
apr run 7

# Знову з кодом
apr run 8 --include-impl
```

**Навіщо це потрібно:**

- GPT бачить розбіжності між дизайном і реалізацією
- Пропонує конкретні покращення коду
- Виявляє архітектурні проблеми в реальному коді

### Моніторинг прогресу

```bash
# Перевірте стан усіх сесій
apr status

# Переглянути аналітику конвергенції
apr stats

# Порівняти результати раундів
apr diff 3 4
```

### Коли зупинятися

**Сигнали конвергенції:**

- Рекомендації стають мінорними
- GPT повторює попередні коментарі
- `apr stats` показує low delta scores
- Ви задоволені якістю специфікації

**Типова кількість раундів:**

- Прості проекти: 5-8 раундів
- Складні системи: 12-20 раундів
- Критично важливі протоколи: 20+ раундів

---

## 📊 Розуміння конвергенції та аналітики

APR збирає метрики для відстеження прогресу вашої специфікації:

### Ключові метрики

```bash
# Переглянути детальну аналітику
apr stats --detailed

# Експортувати в JSON для аналізу
apr stats --json > metrics.json
```

**Що означають метрики:**

- **Word Delta** — зміна розміру між раундами
- **Semantic Similarity** — схожість контенту
- **Recommendation Density** — кількість рекомендацій на одиницю тексту
- **Issue Severity Distribution** — розподіл серйозності проблем

### Інтерактивна панель

```bash
# Запустити TUI панель аналітики
apr dashboard
```

**Навігація в dashboard:**

- `↑/↓` — перегляд метрик
- `Tab` — переключення між панелями
- `q` — вихід

### Експорт даних

```bash
# Експорт в різних форматах
apr stats --export json > analysis.json
apr stats --export csv > analysis.csv
apr stats --export markdown > analysis.md

# Експорт конкретних раундів
apr stats --export json --rounds 1-5 > early_rounds.json
```

> **📖 Детальніше:** [Convergence Analytics в README](README.md#-convergence-analytics).

---

## 🤖 Автоматизація через Robot Mode

Robot Mode — це JSON API для інтеграції APR в автоматизовані pipeline:

### Базове використання

```bash
# Перевірити середовище
apr robot status

# Запустити раунд програмно
apr robot run 5

# Отримати історію у JSON
apr robot history
```

### Інтеграція в скрипти

```bash
#!/bin/bash

# Валідація перед запуском
if ! apr robot validate 3 --quiet; then
    echo "Pre-flight validation failed"
    exit 1
fi

# Запуск раунду
result=$(apr robot run 3)
status=$(echo "$result" | jq -r '.status')

if [ "$status" = "success" ]; then
    echo "Round 3 completed successfully"

    # Інтегрувати результати
    apr integrate 3 --clipboard
else
    echo "Round failed: $(echo "$result" | jq -r '.error')"
    exit 1
fi
```

### CI/CD інтеграція

```yaml
# .github/workflows/spec-review.yml
name: Spec Review
on:
  push:
    paths: ["SPEC.md", "README.md"]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Install APR
        run: |
          curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/automated_plan_reviser_pro/main/install.sh" | bash

      - name: Run automated review
        run: |
          apr robot validate 1 || exit 1
          apr robot run 1

      - name: Upload results
        uses: actions/upload-artifact@v3
        with:
          name: spec-review
          path: .apr/rounds/
```

> **📖 Детальніше:** [Robot Mode в README](README.md#-robot-mode-automation-api).

---

## 🛠️ Налаштування складних workflow

Для складних проектів потрібні кастомні конфігурації workflow:

### Структура конфігурації

```yaml
# .apr/workflows/my-protocol.yaml
name: "Security Protocol v2"
readme_file: "README.md"
spec_file: "docs/protocol-spec.md"
implementation_files:
  - "src/protocol/*.rs"
  - "src/crypto/*.rs"
  - "tests/integration/*.rs"
description: "Zero-knowledge authentication protocol"
```

### Мульти-файлові специфікації

Коли специфікація розділена на кілька файлів:

```yaml
# .apr/workflows/complex-system.yaml
name: "Distributed System"
readme_file: "README.md"
spec_file: "docs/overview.md"
implementation_files:
  - "docs/api-spec.md"
  - "docs/database-schema.md"
  - "docs/security-model.md"
  - "src/core/**/*.go"
```

### Управління workflow

```bash
# Створити новий workflow
apr setup --name backend-api

# Список усіх workflow
apr list

# Запустити з конкретним workflow
apr run 5 --workflow backend-api

# Перемкнутися на інший workflow
cd .apr && ln -sf workflows/backend-api.yaml config.yaml
```

### Кращі практики організації

**Структура проекту:**

```
your-project/
├── .apr/
│   ├── config.yaml -> workflows/main.yaml
│   ├── workflows/
│   │   ├── main.yaml
│   │   ├── security-review.yaml
│   │   └── api-design.yaml
│   └── rounds/
│       ├── main/
│       ├── security-review/
│       └── api-design/
├── docs/
│   ├── spec.md
│   ├── api.md
│   └── security.md
└── src/
```

---

## 🚨 Вирішення проблем та діагностика

Основні проблеми та їх рішення:

### Oracle не запускається

```bash
# Перевірити статус Oracle
oracle status

# Перезапустити Oracle
oracle quit
oracle

# Перевірити версію Node.js (потрібен 18+)
node --version
```

### Сесії "зависають"

```bash
# Перевірити активні сесії
apr status

# Підключитися до активної сесії
apr attach [session-slug]

# Примусово завершити проблемну сесію
oracle quit
```

### Помилки валідації

```bash
# Запустити детальну валідацію
apr run 1 --dry-run

# Перевірити конфігурацію
cat .apr/config.yaml

# Перевірити наявність файлів
apr robot validate 1 --verbose
```

### Проблеми з мережею

```bash
# Увімкнути детальні логи Oracle
export ORACLE_DEBUG=true
apr run 1

# Налаштувати таймаути
export APR_ORACLE_TIMEOUT=180000
export APR_ORACLE_STABILITY_WAIT=15000
```

### Віддалене використання (SSH/headless)

Детальну інструкцію дивіться в [Oracle Remote Setup](README.md#-oracle-remote-setup-headlessssh-environments).

**Швидке налаштування через Tailscale:**

```bash
# На локальній машині
oracle serve --port 3456

# На віддаленому сервері
export ORACLE_URL="http://100.x.x.x:3456"
apr run 1
```

---

## 📚 Додаткові ресурси

### Основна документація

- **[README.md](README.md)** — повна документація з усіма командами та опціями
- **[AGENTS.md](AGENTS.md)** — технічна документація для розробників та інтеграцій

### Корисні розділи README:

- [Usage](README.md#-usage) — повний довідник команд
- [The Workflow](README.md#-the-workflow) — детальний опис робочого процесу
- [Analysis Commands](README.md#-analysis-commands) — команди для аналізу результатів
- [Environment Variables](README.md#-environment-variables) — усі налаштування
- [Troubleshooting](README.md#-troubleshooting) — вирішення проблем

### Інтеграція з інструментами:

- **Oracle** — браузерна автоматизація для ChatGPT
- **Claude Code** — інтеграція з AI-асистентом для кодування
- **MCP Agent Mail** — координація між AI-агентами
- **bv, UBS, ast-grep** — інструменти аналізу коду

### Приклади використання

**Типові сценарії:**

1. **API Design** — ітеративне вдосконалення REST/GraphQL API
2. **Security Protocols** — розробка криптографічних протоколів
3. **System Architecture** — дизайн розподілених систем
4. **Database Schema** — оптимізація структури бази даних

**Реальні проекти:**

- Flywheel Connector Protocol (оригінальний кейс)
- Аутентифікаційні системи
- Протоколи обміну даними
- Мікросервісні архітектури

---

## ❓ Питання та підтримка

**Найчастіші питання:**

1. **Скільки раундів зазвичай потрібно?**
   - Залежить від складності, зазвичай 8-15 раундів

2. **Чи можна використовувати без Oracle?**
   - Ні, Oracle є обов'язковою залежністю

3. **Як працює з приватними проектами?**
   - Усі дані залишаються локальними, відправляється лише те, що ви вказуєте

4. **Чи підтримується робота в команді?**
   - Так, через git можна ділитися `.apr/` директорією

**Де отримати допомогу:**

- GitHub Issues: https://github.com/Dicklesworthstone/automated_plan_reviser_pro/issues
- Документація: [README.md](README.md) та [AGENTS.md](AGENTS.md)

---

**🎯 Готові почати?** Виконайте [Швидкий старт](#швидкий-старт-ваш-перший-робочий-процес) та створіть свій перший workflow!

