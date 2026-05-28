# 🎓 Альма-матер Pro Rails Dev

> **Принцип простой.** Профессионала растит официальная документация и чтение чужого
> хорошего кода, а не марафон курсов. Курсы дают старт, доки — глубину. Поэтому здесь
> первоисточник всегда впереди, а статьи и курсы идут прицепом.
>
> ### 🔑 Документация + практика
>
> Читать доки без кода — иллюзия знания. Писать код без доков — топтание на месте.
> Работает только связка: прочитал → тут же закрепил руками. Тренажёры для ежедневной
> практики — в разделе [«Практика»](#практика-кодом-каждый-день).

### Как пользоваться

Три уровня, по порядку — не пытайся проглотить всё разом, подавишься:

1. **Падаван** — язык Ruby, основы Rails, веб, БД, Git. Фундамент.
2. **Сенсэй** — тесты, фоновые задачи, Hotwire, API, безопасность, деплой.
3. **IndieHacker / MVP** — собрать и выкатить продукт в одиночку.

Дальше — раздел про разработку с ИИ (в 2026-м это базовый навык, а не экзотика) и
справочник: книги, сообщества, статьи, тренажёры, собеседования.

> 💡 Ссылки ведут на `/current`, чтобы не устаревать. На лето 2026 в ходу **Rails 8.1**
> и **Ruby 4.0** (вышел 25.12.2025). Версии всё равно сверяй со своим проектом.

---

# 🥋 Уровень 1. Падаван — фундамент

## Сам язык Ruby (до Rails!)

Частая ошибка новичка — прыгнуть в Rails, не зная Ruby. Так делать не надо: иначе будешь
верить, что `before_action` и `params` — это магия, а не обычные методы.

> ### 💎 Почему Ruby так приятен
>
> Мацумото проектировал язык ради счастья программиста, а не удобства машины — и это
> чувствуется каждый день. Код читается как фраза по-английски (`3.times { puts "hi" }`,
> `users.select(&:active?)`), почти всё — объект, а блоки дают выражать намерение, а не
> церемонию. Работает принцип наименьшего удивления: что кажется логичным, обычно так и
> устроено. Отсюда же растёт и «магия» Rails.

### 🚀 Ruby 4.0 — что нового (релиз к 30-летию языка)

Вышел 25 декабря 2025, в день рождения Ruby. Это не про ломающие изменения, а про задел на годы:

- **ZJIT** — JIT-компилятор нового поколения на Rust, наследник YJIT. Цель — приблизить Ruby к скорости компилируемых языков. *Пока экспериментальный, в прод не торопись.*
- **Ruby Box** — изоляция определений (monkey-patch'ей, глобальных переменных, мутаций библиотек): изолированные тесты, несколько приложений в одном процессе, безопасная проверка чужих гемов.
- **Ractor + `Ractor::Port`** — параллельность без боли GVL, наконец-то честная работа со всеми ядрами.
- **`Set` и `Pathname` стали core-классами** — без `require`, быстрее и легче по памяти.
- **Приятные мелочи:** `Array#rfind`, ускоренный `Array#find`, операторы `&&`/`||` в начале строки продолжают предыдущую.

Короче: ставка на скорость и параллельность — без потери той самой приятности.

- [Документация Ruby (current)](https://docs.ruby-lang.org/en/master/) — **ruby-doc**, главный справочник
- [Анонс Ruby 4.0](https://www.ruby-lang.org/en/news/2025/12/25/ruby-4-0-0-released/) — официальные release notes
- [Стартовая страница языка](https://www.ruby-lang.org/ru/documentation/) — обзоры, в т.ч. «Ruby за 20 минут»
- [Ruby Koans](https://www.rubykoans.com/) — учишь язык, чиня падающие тесты. Лучший способ почувствовать Ruby руками

## Ruby on Rails

- [Rails Guides](https://guides.rubyonrails.org/) — **главное руководство**, читать целиком
- [Rails API Documentation](https://api.rubyonrails.org/) — справочник по всем классам и методам
- [Rails 8.1 Release Notes](https://guides.rubyonrails.org/8_1_release_notes.html) — что нового: Active Job Continuations (джобы по шагам, переживают деплой), встроенный CI `bin/ci`, Structured Event Reporting, редактор **Lexxy** на замену Trix

### 🇷🇺 Как читать доки без английского

Учись читать первоисточник, а не зеркала: переводы отстают по версии и иногда просто
исчезают (rusrails.ru на лето 2026 лежит). Надёжнее переводить официальную доку на лету:

- **Автоперевод браузера** — Chrome/Яндекс, ПКМ → «Перевести страницу». Открываешь [Rails Guides](https://guides.rubyonrails.org/) и читаешь по-русски всегда на свежей версии. Самый практичный путь.
- **Через ИИ** — кинь раздел доки в Claude/любой агент, попроси объяснить по-русски с примерами; заодно сразу спросишь, что непонятно.
- [Документация Ruby на русском](https://www.ruby-lang.org/ru/documentation/) — официальная страница языка
- [railstutorial.ru](https://railstutorial.ru/) — перевод учебника Майкла Хартла
- **rusrails** — сайт лежит, но [исходники на GitHub](https://github.com/rusrails/rusrails/tree/master/source) живы: гайды читаются прямо в markdown

## Стиль кода

- [Ruby Style Guide](https://github.com/rubocop/ruby-style-guide) — стандарт оформления Ruby
- [Rails Style Guide](https://github.com/rubocop/rails-style-guide) — стиль для Rails
- [RuboCop](https://docs.rubocop.org/) — линтер, который проверяет всё это автоматически
- [Style Guide на русском](https://github.com/arbox/ruby-style-guide/blob/master/README-ruRU.md) — *для староверов*

## Веб: фронтенд-основы

- [HTML](https://developer.mozilla.org/ru/docs/Web/HTML) · [CSS](https://developer.mozilla.org/ru/docs/Web/CSS) · [JavaScript](https://developer.mozilla.org/ru/docs/Web/JavaScript) — **MDN**, эталонный справочник
- [TailwindCSS](https://tailwindcss.com/docs/installation/using-vite) — утилитарный CSS, де-факто выбор Rails-комьюнити
- [React](https://react.dev/learn) · [Vue.js](https://vuejs.org/guide/introduction.html) — если понадобится тяжёлый клиент

## Базы данных

- [PostgreSQL](https://www.postgresql.org/docs/current/) — основная боевая БД для Rails
- [SQLite](https://www.sqlite.org/docs.html) — в Rails 8 годится и для продакшена небольших приложений
- [Redis](https://redis.io/docs/latest/) — кэш и брокер для фоновых задач

> 💡 Схему БД сначала рисуй, потом кодь — в голове она не помещается. [**dbdiagram.io**](https://dbdiagram.io/home/)
> описывает схему простым текстом (DBML), а ИИ этот формат отлично генерит: попроси
> модель набросать структуру и сразу увидишь её визуально.

## Git

- [Pro Git (книга на русском)](https://git-scm.com/book/ru/v2) — бесплатно и исчерпывающе

## Docker

- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Гайд по контейнеризации Ruby](https://docs.docker.com/guides/ruby/)

---

# 🥋 Уровень 2. Сенсэй — боевой Rails

## Тестирование

- [Rails Testing Guide](https://guides.rubyonrails.org/testing.html) — встроенный Minitest, начни отсюда
- [RSpec](https://rspec.info/documentation/) — самый популярный фреймворк тестирования в комьюнити
- [Better Specs](https://www.betterspecs.org/) — как писать спеки, за которые не стыдно

## Фоновые задачи

Письма, импорты, отчёты — без этого не живёт почти ни одно реальное приложение.

- [Active Job](https://guides.rubyonrails.org/active_job_basics.html) — абстракция Rails над любым бэкендом задач
- [Solid Queue](https://github.com/rails/solid_queue) — дефолт в Rails 8, очередь поверх БД без Redis
- [Sidekiq](https://github.com/sidekiq/sidekiq/wiki) — проверенный временем стандарт на Redis

## Производительность

- [Active Record Query Guide](https://guides.rubyonrails.org/active_record_querying.html) — как не плодить N+1
- [Bullet](https://github.com/flyerhzm/bullet) — ловит N+1 и лишние запросы прямо в разработке
- [rack-mini-profiler](https://github.com/MiniProfiler/rack-mini-profiler) — профилировщик в углу страницы
- [Strong Migrations](https://github.com/ankane/strong_migrations) — бьёт по рукам перед опасной миграцией на проде

## Hotwire — фронтенд без SPA

- [Turbo](https://turbo.hotwired.dev/handbook/introduction) — скорость SPA почти без JavaScript
- [Stimulus](https://stimulus.hotwired.dev/handbook/introduction) — лёгкий JS для оживления готового HTML
- [Hotwire Native](https://native.hotwired.dev/) — мобильные приложения на той же кодовой базе
- [The Turbo Rails Tutorial (hotrails.dev)](https://www.hotrails.dev/) — **лучший практический туториал по Hotwire**

## API и интеграции

- [Rails как API](https://guides.rubyonrails.org/api_app.html)
- [JSON:API — реализации для Ruby](https://jsonapi.org/implementations/#server-libraries-ruby)
- [GraphQL](https://graphql.org/learn/) · [graphql-ruby](https://graphql-ruby.org/)

## Безопасность

- [Securing Rails Applications](https://guides.rubyonrails.org/security.html) — официальное руководство, обязательно
- [OWASP Top Ten](https://owasp.org/www-project-top-ten/) — карта главных уязвимостей
- [Brakeman](https://brakemanscanner.org/) — статический анализатор безопасности для Rails

## Деплой и CI/CD

Главный сдвиг последних лет — деплой на свои серверы вместо дорогих PaaS. Это идея DHH
(«no-PaaS»), и весь стек Rails 8 построен вокруг неё.

- [**Kamal**](https://kamal-deploy.org/) — деплой Docker-контейнеров на любой сервер по SSH, флагман «no-PaaS»
  - [Документация](https://kamal-deploy.org/docs/installation/) · [Репозиторий (Basecamp/37signals)](https://github.com/basecamp/kamal)
  - 💡 Kamal 2+ деплоит без внешнего registry (Docker Hub/GHCR не обязателен), а секреты берёт прямо из шифрованных credentials Rails.
- [Solid Cache](https://github.com/rails/solid_cache) · [Solid Cable](https://github.com/rails/solid_cable) — кэш и WebSocket поверх БД
- [`bin/ci`](https://guides.rubyonrails.org/8_1_release_notes.html) — встроенный в Rails 8.1 CI (`config/ci.rb`), без облака
- [GitHub Actions](https://docs.github.com/en/actions) — если облачный CI всё-таки нужен
- [Capistrano](https://github.com/capistrano/capistrano) — ветеран деплоя по SSH. Для новых проектов бери Kamal; этот — для не-контейнерных систем

## Микросервисы и обмен сообщениями

> Это про масштаб. Микросервисы умеют превращать одну проблему в распределённую, так что
> сначала освой монолит — большинству его хватает с головой.

- [RabbitMQ для Ruby](https://www.rabbitmq.com/tutorials/tutorial-one-ruby) — официальный туториал
- [Karafka](https://github.com/karafka/karafka) — современный фреймворк Kafka для Ruby
- [SOA на Rails + Kafka](https://habr.com/ru/articles/450028/) — введение на русском

---

# 🚀 Уровень 3. IndieHacker / MVP

## Гибридный фронтенд (рецепты Evil Martians)

Когда Hotwire мало и нужен островок React/Vue/Svelte:

- [Turbo Mount](https://evilmartians.com/chronicles/the-art-of-turbo-mount-hotwire-meets-modern-js-frameworks) — точечная вставка JS-компонентов в Hotwire
- [Inertia.js](https://inertiajs.com/) — ощущение SPA без отдельного API
- [Vite Ruby](https://vite-ruby.netlify.app/) — современная сборка фронтенда для Rails

## Гемы, которые стоит знать

- **[Devise](https://github.com/heartcombo/devise)** — аутентификация (хотя в Rails 8 есть и встроенный генератор)
- **[Pundit](https://github.com/varvet/pundit)** — авторизация по политикам
- **[rails-erd](https://github.com/voormedia/rails-erd)** — ER-диаграммы по моделям
- **[Typelizer](https://github.com/skryukov/typelizer)** — генерация TypeScript-типов из Rails (Evil Martians)
- **[ffaker](https://github.com/ffaker/ffaker)** — генерация тестовых данных
- **[Discourse](https://github.com/discourse/discourse)** — большой Rails-проект, который можно читать как учебник

---

# 🤖 Разработка с ИИ

В 2026-м это часть ремесла, как когда-то Git. Причём Rails для ИИ — подарок:
convention-over-configuration делает структуру предсказуемой, и первая догадка модели о
том, где лежит код, обычно верна. Ruby к тому же один из самых токен-эффективных языков
для агентов.

> 🔑 ИИ не отменяет принцип этой базы, а усиливает его: модель ошибается ровно там, где
> ты сам не понимаешь доку. Порядок — **документация → практика → ИИ**. Агент ускоряет
> того, кто знает фундамент, и уверенно топит того, кто не знает.

## Агенты в терминале

- [**Claude Code**](https://docs.claude.com/en/docs/claude-code/overview) — агент Anthropic в терминале: правит файлы, гоняет тесты, ведёт целые задачи
- [**OpenCode**](https://opencode.ai/) — открытый агент для терминала ([репозиторий](https://github.com/opencode-ai/opencode)): подключается к любой модели — Claude, GPT, Gemini или локальной
- [Qwen Code](https://github.com/QwenLM/qwen-code) — открытый терминальный агент от команды Qwen
- [Cursor](https://cursor.com/) — AI-first IDE (форк VS Code), если ближе редактор, а не терминал

## Открытые и локальные модели

Если важны приватность, отсутствие облака или экономия — открытые веса уже догнали проприетарные.

- [**Ollama**](https://ollama.com/) — простейший способ запустить модель локально; связка **OpenCode + Ollama** даёт агента без облака
- [Каталог открытых coding-моделей (2026)](https://kilo.ai/open-source-models) — актуальный обзор
- На лето 2026 на слуху: **Qwen3-Coder**, **DeepSeek V4**, **GLM**, **Kimi K2**, **Devstral**. Для локального старта обычно советуют Qwen-Coder или Devstral; тяжёлое тянут DeepSeek/GLM/Kimi

## Rails + ИИ: рецепты

- [claude-on-rails](https://github.com/obie/claude-on-rails) — фреймворк для Rails на Claude Code от Оби Фернандеса
- [rails-instructions](https://github.com/levifig/rails-instructions) — «DHH-driven» правила для любого агента (Cursor, Copilot, Claude)
- [thoughtbot: Claude Skill для аудита Rails-кода](https://thoughtbot.com/blog/ai-in-focus:a-new-claude-skill-for-rails-code-audits)
- **MCP** ([Model Context Protocol](https://modelcontextprotocol.io/)) — открытый стандарт Anthropic: подключает агента к БД, гиту, деплою и берёт только нужный контекст

> 💡 Главный конфиг — `CLAUDE.md` (или `.cursor/rules`) в корне: соглашения, архитектура,
> правила тестов. Удобно, что та же документация в Obsidian кормит и тебя, и ИИ.

---

# 📚 Справочник

## Книги

- **Sandi Metz — _Practical Object-Oriented Design in Ruby (POODR)_** — must-read по объектному проектированию
- **thoughtbot — [_Ruby Science_](https://thoughtbot.com/ruby-science/)** — рефакторинг и код-смеллы на живых примерах
- **Роман Пушкин — _Ruby для романтиков_** — мягкий заход в язык для начинающих

## Видео

- [DHH — презентация Rails 8](https://www.youtube.com/watch?v=-cEn_83zRFw) — больше шоу, но заряжает

## Сообщества

- [Rails Discuss](https://discuss.rubyonrails.org/)
- [Hotwire Discussion](https://discuss.hotwired.dev/)

## Статьи

- [Ruby on Rails Design Patterns 101](https://medium.com/@slimbennasrallah_89177/ruby-on-rails-design-patterns-101-d99f43adc2b3)
- [Deploying review apps with Kamal on CI/CD](https://guillaumebriday.fr/deploying-review-apps-automatically-with-kamal-on-ci-cd)
- [Перевод Rails-приложения через OpenAI](https://guillaumebriday.fr/how-i-use-openai-to-translate-my-rails-application-into-multiple-languages)
- [Почему я рекомендую Rails новичкам](https://habr.com/ru/articles/794476/) — Хабр

> Блоги, которые стоит читать целиком: [Evil Martians](https://evilmartians.com/chronicles),
> [thoughtbot](https://thoughtbot.com/blog), [GoRails](https://gorails.com/).

## Алгоритмы

- [Грокаем алгоритмы — код примеров](https://github.com/egonSchiele/grokking_algorithms)
- [Sorting Algorithms with Ruby](https://dev.to/daviducolo/sorting-algorithms-with-ruby-4o18)
- [Алгоритмы и структуры данных (видео, Ilya Krukowski)](https://www.youtube.com/playlist?list=PLWlFXymvoaJ-Q8FyOj9SQ3Eoog5Nkv0lI)

## Практика кодом каждый день

Вторая половина формулы. Заведи привычку: одна задача в день — и руки начинают думать быстрее головы.

- [Codewars](https://codewars.com/) — **рекомендую сильнее всего**, прокачка как игра, есть Ruby
- [Exercism — Ruby track](https://exercism.org/tracks/ruby) — задачи с менторскими ревью, бесплатно
- [LeetCode](https://leetcode.com/) — классика для алгоритмических собеседований
- [Codeforces](https://codeforces.com/) — спортивное программирование
- [Replit](https://replit.com/) — быстро пописать код в браузере без настройки окружения

## Тренажёры продуктивности

- [keybr.com](https://www.keybr.com/) — слепая печать
- **Vim:** [openvim](https://openvim.com/) (тренажёр) · [PacVim](https://github.com/jmoon018/PacVim) (игра)

## Проектирование и документация

- [dbdiagram.io](https://dbdiagram.io/home/) — схемы БД текстом (DBML), ИИ хорошо генерит этот формат
- [Miro](https://miro.com/) — удобно для архитектуры и набросков
- [Draw.io](https://www.drawio.com/) — простой и бесплатный

> 💡 Документацию проекта веди в [Obsidian](https://obsidian.md/) — так советует Андрей
> Карпаты (Andrej Karpathy). Это локальные markdown-заметки, связанные ссылками `[[ ]]` в
> граф. Бонус: те же заметки потом кормят ИИ.

---

# 🎓 Курсы — если совсем с нуля

> Курсы хороши для старта. Освоился — переходи к докам выше, дальше растут на них.

**Бесплатные, для начала:**
- [Code Basics — Ruby](https://code-basics.com/ru/languages/ruby) — open-source основы от Hexlet
- [The Odin Project — Full Stack Ruby on Rails](https://www.theodinproject.com/paths/full-stack-ruby-on-rails) — полный бесплатный путь (англ.)
- [Курс Романа Пушкина](https://rubyschool.us/) — бесплатный, слегка устаревший, но добротный

**По подписке, когда нужны практика и видео:**
- [GoRails](https://gorails.com/series) · [Hexlet](https://ru.hexlet.io/courses_ruby)

---

# 💼 Подготовка к собеседованиям

> «Пройти собес» ≠ «стать профи» — это разные задачи. Бери этот раздел после фундамента.

- [Hexlet — вопросы по Rails](https://github.com/Hexlet/ru-interview-questions/blob/main/questions/rails.md)
- [EVRONE Challenge — самопроверка](https://challenge.career.evrone.com/challenge_modules/ruby-on-rails/)
- [Rails Interview Questions (англ., с ответами)](https://github.com/gardeziburhan/rails_interview_questions)
- [Шпаргалка по основам Backend](https://github.com/DEBAGanov/interview_questions/blob/main/1.%20%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B%20Backend-%D1%80%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B8.md)
