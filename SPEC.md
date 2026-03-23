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

### Cards (cases)
- Background: surface color with subtle border
- Hover: translateY(-4px) + shadow deepens + border accent color
- Tags: pill style, accent color with low opacity background
- Media zone below description:
  - type: image → static screenshot (max-height: 280px, object-fit: cover)
  - type: video → static thumbnail + play button overlay → opens YouTube in new tab
  - type: both → image first, then "Watch demo →" button below (opens YouTube)
  - type: none → text only

### Sections layout (top to bottom)
1. Hero (name, tagline, CTA)
2. Cases (grid, 2 columns on desktop / 1 on mobile)
3. Stack / Technologies
4. How we work (3 steps)
5. Testimonials
6. Final CTA
7. Footer (Telegram + GitHub + LinkedIn)

---

## Cases — full list

### Keep (already on site, update text only):
1. **Аудит документов**
   Tags: n8n, Google Drive, Google Sheets
   Media: type: image → img/workflow-audit.jpg
   Text: "100+ подрядчиков, Google Drive, 3 обязательных файла у каждого —
   проверка вручную занимала 3 дня. Теперь воркфлоу делает это за 5 минут
   по расписанию."

2. **Задачи из Telegram**
   Tags: Telegram API, AI
   Media: type: none
   Text: "Дизайн-студия в Дубае теряла задачи в групповых чатах. Бот читает
   сообщения, извлекает задачи через AI и пушит в Todoist. Ноль потерь."

3. **AI-агент для косметологии**
   Tags: RAG, Bitrix24, AI
   Media: type: none
   Text: "Мультиплатформенный RAG-агент для косметологической клиники: работает
   в Telegram, WhatsApp и открытых линиях Битрикса. Выявляет потребности
   клиента, консультирует по базе знаний, автоматически создаёт контрагента
   в Битрикс24 и уведомляет менеджера."

4. **Платёжная интеграция Mercado Pago**
   Tags: Python, API
   Media: type: none
   Text: "Интеграция Mercado Pago для аргентинского клиента — локализованный
   платёжный флоу под латиноамериканский рынок."

5. **Корпоративное обучение n8n + AI** (rewritten)
   Tags: n8n, AI, обучение
   Media: type: image → img/training-session.jpg
   Text: "Логистическая компания, бухгалтерия — 5 человек, нулевой технический
   бэкграунд. 12 сессий удалённо. После второго занятия команда самостоятельно
   собирала воркфлоу с Gmail + AI Agent + conditional logic. Формат: обучение
   под конкретные задачи компании, не абстрактный курс."

### New cases to add:

6. **Платёжные поручения без ручного ввода**
   Tags: n8n, СБИС, T-Банк API
   Media: type: image → img/workflow-sbis-tbank.jpg
   Text: "Магазин автозапчастей в Санкт-Петербурге: каждая приходная накладная
   из СБИС требовала ручного создания платёжного поручения в Т-Банке. Теперь
   накладная автоматически создаёт готовое поручение через API Т-Банка.
   Ноль ручного ввода, ноль ошибок транскрипции."

7. **Мониторинг конкурентов**
   Tags: Python, PostgreSQL, Streamlit, Telegram Bot
   Media: type: image → img/dashboard-competitors.jpg
   Text: "Компания в строительном рынке отслеживала 20 подрядчиков и 2400+
   объявлений через громоздкий .exe на 500MB с ручным запуском. Заменил на
   веб-дашборд с фильтрами, аналитикой цен и Telegram-алертами на изменения.
   Система живёт на сервере и обслуживает себя сама."

8. **Семантический поиск по видеоархиву**
   Tags: Python, Gemini Flash, Qdrant, FFmpeg
   Media: type: both
     image → img/semantic-search-demo.jpg
     video → https://youtube.com/shorts/lX34W1ZhJH4
   Text: "ТВ-журналист с архивом сотен часов съёмок не мог найти нужный момент.
   Построил систему: FFmpeg извлекает кадры → Gemini описывает их → Qdrant
   хранит векторы. Запрос 'красный Корвет на брусчатке' находит нужный кадр
   без знания точных слов из описания. Стоимость индексации: ~$5–7 за 100
   часов видео."

9. **Telegram как CRM**
   Tags: Make, Telegram Bot API
   Media: type: none
   Text: "Малый бизнес терял переписку с клиентами в личных сообщениях бота.
   Настроил систему на супергруппе с топиками: каждый клиент получает отдельный
   тред с полной историей. Команда отвечает прямо в Telegram — без CRM, без
   новых инструментов, без обучения."

---

## New sections

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

### Footer
- t.me/alekseenko_ai (already exists)
- github.com/ilia-alekseenko-work (add)
- linkedin.com/in/ilya-alekseenko-147492268 (add)

---

## EN version (separate page /en)
- Separate file: en.html
- Same structure, full English translation
- Lang switcher in header: RU | EN
- Do after RU version is complete

---

## Media files needed
| File | Status |
|------|--------|
| img/photo.jpg | ✅ ready (moved from root) |
| img/workflow-sbis-tbank.jpg | ✅ ready |
| img/dashboard-competitors.jpg | ✅ ready |
| img/workflow-audit.jpg | ✅ ready  |
| img/training-session.jpg | ✅ ready  |
| img/semantic-search-demo.jpg | ✅ ready  |

---

## Definition of done
- [ ] Full visual redesign implemented
- [ ] All 9 cases present with correct media
- [ ] Stack block added
- [ ] How we work block added
- [ ] Footer with all 3 links
- [ ] Mobile looks correct
- [ ] git commit + git push + git pull on server
- [ ] EN version (separate session)
