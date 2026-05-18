# SPEC.md — site-ai-integrator v2

## Goal
Full redesign of the AI integrator portfolio site.
Convey technical expertise, add 6 new cases with media support,
add new sections. Keep it fast, clean, no frameworks.

## Tech constraints
- Pure HTML / CSS / JS — no build step, no frameworks
- Must work correctly on mobile
- No external dependencies except Google Fonts

## Out of scope (separate future project)
- Backend / contact form
- CMS

---

## Visual redesign

### Color scheme
- Background: dark (#0f0f0f or #111318)
- Surface (cards): #1a1a1f
- Accent: electric blue or cyan (#4f8ef7 or #00d4aa) — one accent only
- Text primary: #f0f0f0
- Text secondary: #8a8a9a
- Border: 1px solid rgba(255,255,255,0.08)

### Typography
- Keep current font or switch to Inter (Google Fonts)
- Hero headline: large, bold, tight line-height
- Body: 16px, comfortable line-height

### Cards (regular cases)
- Background: surface color with subtle border
- Hover: translateY(-4px) + shadow deepens + border accent color
- Tags: pill style, accent color with low opacity background
- Media zone below description:
  - type: image → static screenshot (max-height: 280px, object-fit: cover)
  - type: video → static thumbnail + play button overlay → opens YouTube in new tab
  - type: both → image first, then "Watch demo →" button below (opens YouTube)
  - type: none → text only

### Flagship cases (full-width with attached testimonial)
- Full container width (not part of the 2-column grid)
- Internal layout: text + media (image or image-grid) + attached testimonial block below
- Media:
  - single image → right side on desktop, below text on mobile
  - image-grid (2 screenshots) → side-by-side row below text, stack on mobile
- Testimonial block attached visually (no gap, shared border or subtle divider only):
  - ★★★★★ rating
  - Testimonial text (quoted, trimmed if long)
  - Author name + source (e.g. "Avito")
  - Original review screenshot displayed alongside or below the quoted text —
    makes it clear it's a real Avito review, not paraphrased

### Sections layout (top to bottom)
1. Hero (name, tagline, CTA)
2. **Обо мне** ✅ DONE — already deployed
3. **Кейсы** — flagship cases (2x full-width with testimonials) → divider → regular cases (grid)
4. Stack / Technologies
5. How we work (3 steps)
6. Testimonials (short ones — without Ksenia & Fyodor, those are now attached to their cases)
7. Final CTA
8. Footer (Telegram + GitHub + LinkedIn)

---

## Cases — full list (NEW ORDER)

### Flagship cases — full-width with attached testimonials

#### F1. Корпоративное обучение n8n + AI
   Format: flagship (full-width + attached testimonial)
   Layout: image-top (full-width image first, text below, testimonial attached)
   Tags: n8n, AI, обучение

   Main media: img/training-session.jpg
   - Full width of the card container
   - max-height: 480px
   - object-fit: contain (NOT cover — content must not be cropped;
     image contains an n8n workflow canvas + video call participants,
     cropping would lose important content)
   - Rounded corners matching the card surface

   Body text (placed below the image, single column, max-width ~720px,
   centered within the card):

   "Бухгалтерия французской логистической группы — 5 человек, нулевой
   технический бэкграунд. 12 онлайн-сессий, работа на реальных задачах
   компании, не абстрактный курс.

   Что освоили:
   → Учёт запросов из Gmail в Google Таблицах с уведомлениями
   → Аналитика входящих сообщений: кто, когда, сроки ответа
   → AI-агент, который читает рассылки, делает выжимки и сохраняет в Sheets
   → Настройка AI-узлов (OpenRouter, Claude, Gemini) и оптимизация промптов

   После второго занятия команда самостоятельно собирала воркфлоу
   с Gmail + AI Agent + conditional logic. Сейчас планируют интеграцию
   n8n с 1С."

   Testimonial (attached below the body, separated by a thin divider line
   only — no card gap, same card surface continues):

   Stars: ★★★★★

   Quoted text (SHORTENED — do not use the full review):
   "Илья оказывал оперативную консультационную поддержку в Telegram
   между занятиями. Очень довольны профессионализмом и практическим
   подходом. Рекомендуем как компетентного специалиста по обучению
   и консалтингу n8n."

   Author line: Ксения Маликова · Avito · 3 апреля 2026

   Review screenshot: img/fm-review.jpg
   - Placed BELOW the quoted text and author line (not next to them)
   - Compact thumbnail size on desktop (max-width ~360px, max-height ~200px,
     object-fit: contain)
   - Clickable: wraps in <a href="img/fm-review.jpg" target="_blank"
     rel="noopener"> — opens full-size in new tab
   - Cursor: pointer on hover, subtle opacity transition on hover
   - No lightbox library — native browser image preview is enough
   - Mobile: full container width, max-height ~240px

#### F2. Тутор-бот по химии
   Format: flagship (full-width + attached testimonial)
   Layout: image-top (image-grid first, text below, testimonial attached)
   Tags: n8n, Telegram Bot API, Claude, PostgreSQL, Google Sheets API

   Main media: image-grid of 2 screenshots
   Files:
     - img/fedor-bot-task.jpg (task request with filters)
     - img/fedor-bot-lesson.jpg (lesson info reply)
   Layout:
     - Desktop: 2 columns, gap ~16-24px, equal width (1fr 1fr)
     - Each image: max-height ~360px, object-fit: contain (NOT cover —
       Telegram screenshots contain text that must not be cropped)
     - Mobile (<768px): stack vertically, full container width each,
       max-height ~280px each
     - Rounded corners matching the card surface
     - No captions under the images

   Body text (placed below the image-grid, single column, max-width ~720px,
   centered within the card — same pattern as F1):

   "Репетитор по химии ведёт несколько учеников параллельно: у каждого
   своя программа, свой прогресс, свои пробелы. Подобрать задание вручную
   — открыть банк задач, вспомнить что уже проходили, учесть сложность,
   не повторить темы. На каждого ученика, каждое занятие.

   Написали Telegram-бота на n8n:
   → Выдаёт задания по номеру, теме и сложности — темы с `!` исключаются автоматически
   → Отдельный режим для пробных занятий: задание → ответ → разбор в строгом порядке
   → Информация по каждому занятию: оплата, дата, домашнее задание, оценки, ссылка на запись
   → Поддерживает несколько номеров билетов в одном запросе
   → Планировщик отслеживает прогресс каждого ученика каждые 10 минут

   Сдано раньше срока. После сдачи клиент возвращался дважды: добавили
   модуль случайного выбора заданий с фильтрами по сложности и
   Include/Exclude логикой, а потом переписали сборку пробного экзамена —
   раньше шёл loop из 34 последовательных запросов к Google Sheets
   (по одному на каждый лист), теперь один batch-запрос за всё. Скорость
   сборки выросла примерно в 12 раз, ушли спорадические ошибки от
   rate limit."

   Testimonial (attached below the body, same pattern as F1 —
   thin divider line, no card gap, same card surface):

   Stars: ★★★★★

   Quoted text (SHORTENED — do not use the full review):
   "Илья предложил заменить узлы ИИ на код там, где это было не очень
   эффективно, — ускорило работу и уменьшило стоимость процесса.
   Рекомендую специалиста, буду обращаться ещё."

   Author line: Фёдор Васильевич · Avito · 3 апреля 2026

   Review screenshot: img/fedor-review.jpg (optional — include if file exists)
   - Same behavior as F1: clickable thumbnail below the author line,
     max-width ~360px, max-height ~200px on desktop, full-width on mobile
   - Wraps in <a href="img/fedor-review.jpg" target="_blank" rel="noopener">
   - If the file doesn't exist yet, skip this element (testimonial works
     fine without it; F1 has it because the file was ready)

### Regular cases — 2-column grid below flagships, separated by divider "Другие проекты"

NOTE: cases with screenshots come first (R1–R5), then text-only cases (R6–R8).
This avoids visual gaps in the grid where some cards have media and others don't.

#### R1. Аудит документов
   Tags: n8n, Google Drive, Google Sheets
   Media: type: image → img/workflow-audit.jpg
   Text: "Каждый квартал бухгалтерия вручную проверяла 100+ подрядчиков:
   у каждого должны быть 3 обязательных документа в Google Drive.
   Структура папок: Год → Квартал → Подрядчик → Объект. Сотни папок,
   ручная проверка, высокий риск ошибки — 3 дня работы.

   Автоматизация на n8n:
   → Берёт актуальный список объектов из Google Sheets
   → Сканирует структуру папок Drive
   → Проверяет наличие каждого из 3 файлов
   → Логирует отсутствующие документы
   → Формирует отчёт о расхождениях и отправляет ссылку руководителю

   Результат: 3 дня → 5 минут по расписанию. Точность 100% — система
   не устаёт и не пропускает файлы."

#### R2. Мониторинг конкурентов
   Tags: Python, PostgreSQL, Streamlit, Telegram Bot
   Media: type: image → img/dashboard-competitors.jpg
   Text: "Компания в строительном рынке отслеживала 20 подрядчиков и 2400+
   объявлений через громоздкий .exe на 500MB с ручным запуском. Заменил на
   веб-дашборд с фильтрами, аналитикой цен и Telegram-алертами на изменения.
   Система живёт на сервере и обслуживает себя сама."

#### R3. Платёжные поручения без ручного ввода
   Tags: n8n, СБИС, T-Банк API
   Media: type: image → img/workflow-sbis-tbank.jpg
   Text: "Магазин автозапчастей в Санкт-Петербурге: каждая приходная накладная
   из СБИС требовала ручного создания платёжного поручения в Т-Банке. Теперь
   накладная автоматически создаёт готовое поручение через API Т-Банка.
   Ноль ручного ввода, ноль ошибок транскрипции."

#### R4. Семантический поиск по видеоархиву
   Tags: Python, Gemini Flash, Qdrant, FFmpeg
   Media: type: both
     image → img/semantic-search-demo.jpg
     video → https://youtube.com/shorts/lX34W1ZhJH4
   Text: "ТВ-журналист с архивом сотен часов съёмок не мог найти нужный момент.
   Построил систему: FFmpeg извлекает кадры → Gemini описывает их → Qdrant
   хранит векторы. Запрос 'красный Корвет на брусчатке' находит нужный кадр
   без знания точных слов из описания. Стоимость индексации: ~$5–7 за 100
   часов видео."

#### R5. Задачи из Telegram для команды
   Tags: n8n, Telegram Bot API, OpenAI Whisper, GPT-4.1-mini, Todoist API
   Media: type: image → img/Danil-todoist.jpg
   Text: "Девелоперская компания в Дубае: команда из 10 человек,
   16 параллельных проектов, общение в Telegram. Руководитель надиктовывает
   голосом или текстом — задача должна оказаться в Todoist у нужного
   сотрудника в нужном проекте, без ручной перепечатки.

   Telegram-бот на n8n:
   → Принимает текст и голосовые — голосовые расшифровывает через Whisper
   → GPT-4.1-mini вытягивает из сообщения суть: что сделать, кто
     ответственный, в каком проекте, к какому сроку
   → Гибкое сопоставление имён сотрудников — русские падежи, прозвища,
     сокращения
   → Названия проектов узнаются по тому, как их реально называют
     в команде, а не только по официальным именам
   → Каждый сотрудник работает под своим Todoist-токеном — токены
     хранятся в .env на сервере, бот выбирает нужный по telegram_id

   Клиент вернулся через полгода после первого проекта (Telegram-бот
   для отслеживания обязательств в групповых чатах). Сейчас Todoist-
   интеграция в финале тестирования."

#### R6. AI-агент для косметологии
   Tags: RAG, Bitrix24, AI
   Media: type: none
   Text: "Мультиплатформенный RAG-агент для косметологической клиники: работает
   в Telegram, WhatsApp и открытых линиях Битрикса. Выявляет потребности
   клиента, консультирует по базе знаний, автоматически создаёт контрагента
   в Битрикс24 и уведомляет менеджера."

#### R7. Telegram как CRM
   Tags: Make, Telegram Bot API
   Media: type: none
   Text: "Малый бизнес терял переписку с клиентами в личных сообщениях бота.
   Настроил систему на супергруппе с топиками: каждый клиент получает отдельный
   тред с полной историей. Команда отвечает прямо в Telegram — без CRM, без
   новых инструментов, без обучения."

#### R8. Платёжная интеграция Mercado Pago
   Tags: Python, API
   Media: type: none
   Text: "Интеграция Mercado Pago для аргентинского клиента — локализованный
   платёжный флоу под латиноамериканский рынок."

---

## Other sections (unchanged)

### Stack block
Title: "Инструменты"
Items: n8n · Make · Python · FastAPI · Claude API · OpenAI ·
       Gemini · Telegram Bot API · Bitrix24 · AmoCRM ·
       PostgreSQL · Qdrant · Docker · T-Банк API · СБИС

### How we work (3 steps)
Title: "Как мы работаем"
1. Созвон 15 минут — разбираем задачу, ничего не продаём
2. Предложение: стек, сроки, стоимость — фиксированная цена
3. Разработка и сдача с документацией

### Testimonials (short, bottom of page)
Title: "Что говорят клиенты"
Keep only short testimonials (Анатолий, Андрей, Анастасия, Сергей, Игорь).
Do NOT include Ksenia and Fyodor here — they are attached to their cases above.

### Footer
- t.me/alekseenko_ai
- github.com/ilia-alekseenko-work
- linkedin.com/in/ilia-alekseenko   ← UPDATED URL (was /ilya-alekseenko-147492268)

---

## EN version (separate page /en)
- Separate file: en.html
- Same structure, full English translation
- Lang switcher in header: RU | EN
- Do after RU version is complete

---

## Media files needed
| File | Status | Used in |
|------|--------|---------|
| img/photo.jpg | ✅ ready | Hero |
| img/workflow-audit.jpg | ✅ ready | R1 |
| img/dashboard-competitors.jpg | ✅ ready | R2 |
| img/workflow-sbis-tbank.jpg | ✅ ready | R3 |
| img/semantic-search-demo.jpg | ✅ ready | R4 |
| img/Danil-todoist.jpg | ✅ ready | R5 (new) |
| img/training-session.jpg | ✅ ready | F1 |
| img/fm-review.jpg | ✅ ready | F1 testimonial screenshot |
| img/fedor-bot-task.jpg | 🆕 to add | F2 (screenshot of task request) |
| img/fedor-bot-lesson.jpg | 🆕 to add | F2 (screenshot of lesson info) |
| img/fedor-review.jpg | 🆕 optional | F2 testimonial screenshot |

---

## Definition of done
- [x] "Обо мне" section deployed
- [ ] Flagship case format implemented (full-width + attached testimonial)
- [ ] Case F1 (Корпоративное обучение) added with Ksenia testimonial + fm-review.jpg
- [ ] Case F2 (Тутор-бот по химии) added with Fyodor testimonial + 2 bot screenshots
- [ ] Regular cases reordered (R1–R8): screenshots first, text-only after
- [ ] Case R5 (Задачи из Telegram) rewritten with expanded text + Danil-todoist.jpg
- [ ] Divider "Другие проекты" added between flagships and regular cases
- [ ] Short testimonials block updated (Ksenia & Fyodor removed from bottom)
- [ ] Stack block updated
- [ ] How we work block updated
- [ ] Footer LinkedIn URL updated to linkedin.com/in/ilia-alekseenko
- [ ] Mobile looks correct (flagships stack vertically, image grid stacks)
- [ ] git commit + git push + git pull on server
- [ ] EN version (separate session)
