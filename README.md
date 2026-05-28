# 🎓 Альма-матер Pro Rails Dev

> **Принцип этой базы.** Профессионала делает официальная документация и чтение
> чужого хорошего кода — а не марафон курсов. Курсы дают старт, доки дают глубину.
> Поэтому здесь на первом месте всегда первоисточник, а курсы и статьи — приложением.
>
> ### 🔑 ДОКУМЕНТАЦИЯ + ПРАКТИКА = ключ к успеху
>
> Читать доки без кода — иллюзия знания. Писать код без доков — топтание на месте.
> Сила в связке: прочитал раздел → сразу закрепил руками. Поэтому в этой базе на
> каждый теоретический блок есть куда применить — а отдельный набор тренажёров для
> ежедневной практики собран ниже в разделе [«Практика»](#практика-кодом-каждый-день).

### Как пользоваться

Материал разбит на три уровня. Не пытайся проглотить всё сразу — иди по порядку:

1. **Падаван** — язык Ruby, основы Rails, веб, БД, Git. Фундамент.
2. **Сенсэй** — тестирование, фоновые задачи, Hotwire, API, безопасность, деплой.
3. **IndieHacker / MVP** — собрать и выкатить продукт в одиночку.

После трёх уровней — отдельный блок про **AI-ассистированную разработку**: в 2026-м
это уже не опция, а базовый навык. Ниже — справочные разделы: книги, сообщества,
статьи, тренажёры, подготовка к собеседованиям. Это уже по потребности.

> 💡 Где можно — ссылки ведут на `/current` или последнюю версию доки, чтобы не
> устаревать. На лето 2026 актуальны **Rails 8.1** и **Ruby 4.0** (вышел 25.12.2025).
> Версию языка/фреймворка всегда сверяй со своим проектом.

---

# 🥋 Уровень 1. Падаван — фундамент

## Сам язык Ruby (до Rails!)

Частая ошибка новичка — прыгнуть сразу в Rails, не зная Ruby. Не делай так.

> ### 💎 Почему Ruby — один из самых приятных языков в мире
>
> Девиз Ruby — **«счастье программиста»** (Matz проектировал язык так, чтобы он
> радовал человека, а не машину). Это не лозунг, а ощутимое каждый день свойство:
> код читается как английская фраза (`3.times { puts "hi" }`, `users.select(&:active?)`),
> почти всё — объект, а блоки и метапрограммирование позволяют выражать намерение, а
> не церемонию. Отсюда же растёт магия Rails. **Принцип наименьшего удивления**:
> то, что кажется логичным, обычно и работает. Ruby оптимизирован под радость —
> поэтому на нём так приятно прототипировать и так легко возвращаться к коду спустя
> полгода.

### 🚀 Ruby 4.0 — что нового и зачем (релиз к 30-летию языка)

Вышел 25 декабря 2025, в день рождения Ruby. Это не про «ломающие изменения», а про
закладку фундамента на годы вперёд:

- **ZJIT** — JIT-компилятор нового поколения (наследник YJIT, на Rust). В долгосрок это путь к тому, чтобы Ruby приближался к скорости компилируемых языков, не теряя своей выразительности. *Пока экспериментальный — в прод не торопись.*
- **Ruby Box** — изоляция определений (monkey-patch'ей, глобальных переменных, мутаций библиотек). Открывает изолированные тесты, запуск нескольких приложений в одном процессе и безопасную оценку чужих гемов. Большой задел на будущее.
- **Ractor + `Ractor::Port`** — взросление настоящей параллельности без GVL-боли. Долгосрочно — честное использование многоядерности.
- **`Set` и `Pathname` стали core-классами** — без `require`, быстрее и экономнее по памяти.
- **Мелочи радости:** `Array#rfind`, ускоренный `Array#find`, логические операторы (`&&`, `||`) в начале строки продолжают предыдущую — код становится чище.

> 💡 Итог: Ruby 4 — это ставка на **скорость (ZJIT) и параллельность (Ractor)** при
> сохранении той самой приятности. Язык готовят к следующему десятилетию.

- [Документация Ruby (current)](https://docs.ruby-lang.org/en/master/) — **ruby-doc**, главный справочник
- [Анонс Ruby 4.0](https://www.ruby-lang.org/en/news/2025/12/25/ruby-4-0-0-released/) — официальные release notes
- [Официальная стартовая страница языка](https://www.ruby-lang.org/ru/documentation/) — обзорные материалы, в т.ч. «Ruby за 20 минут»
- [Ruby Koans](https://www.rubykoans.com/) — учишь язык, проходя падающие тесты. Лучший способ почувствовать Ruby руками

## Ruby on Rails

- [Rails Guides](https://guides.rubyonrails.org/) — **главное руководство**, читать целиком
- [Документация Rails на русском](https://rusrails.ru/) — перевод гайдов, для старта на родном
- [Rails API Documentation](https://api.rubyonrails.org/) — справочник по всем классам и методам
- [Rails 8.1 Release Notes](https://guides.rubyonrails.org/8_1_release_notes.html) — что нового: Active Job Continuations (джобы по шагам, переживают деплой), встроенный CI `bin/ci`, Structured Event Reporting (телеметрия), редактор **Lexxy** на замену Trix

## Стиль кода

- [Ruby Style Guide](https://github.com/rubocop/ruby-style-guide) — стандарт оформления Ruby
- [Rails Style Guide](https://github.com/rubocop/rails-style-guide) — стиль для Rails
- [RuboCop](https://docs.rubocop.org/) — линтер, который проверяет соблюдение этих гайдов автоматически
- [Style Guide на русском](https://github.com/arbox/ruby-style-guide/blob/master/README-ruRU.md) — *для староверов*

## Веб: фронтенд-основы

- [HTML](https://developer.mozilla.org/ru/docs/Web/HTML) · [CSS](https://developer.mozilla.org/ru/docs/Web/CSS) · [JavaScript](https://developer.mozilla.org/ru/docs/Web/JavaScript) — **MDN**, эталонный справочник
- [TailwindCSS](https://tailwindcss.com/docs/installation/using-vite) — утилитарный CSS, де-факто выбор Rails-комьюнити
- [React](https://react.dev/learn) · [Vue.js](https://vuejs.org/guide/introduction.html) — если понадобится тяжёлый клиент

## Базы данных

- [PostgreSQL](https://www.postgresql.org/docs/current/) — основная боевая БД для Rails
- [SQLite](https://www.sqlite.org/docs.html) — в Rails 8 пригоден и для продакшена небольших приложений
- [Redis](https://redis.io/docs/latest/) — кэш и брокер для фоновых задач

> 💡 **Схему БД сначала рисуй, потом кодь.** Онлайн-сервисы дают наглядность, которой
> не хватает в голове. [**dbdiagram.io**](https://dbdiagram.io/home/) — мой выбор: схема
> описывается простым текстом (DBML), а ИИ отлично генерит этот формат — можно попросить
> модель набросать структуру и сразу увидеть её визуально.

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
- [Better Specs](https://www.betterspecs.org/) — соглашения о том, как писать хорошие спеки

## Фоновые задачи

Без этого не обходится почти ни одно реальное приложение — письма, импорты, отчёты.

- [Active Job](https://guides.rubyonrails.org/active_job_basics.html) — абстракция Rails над любым бэкендом задач
- [Solid Queue](https://github.com/rails/solid_queue) — дефолт в Rails 8, очередь поверх БД без Redis
- [Sidekiq](https://github.com/sidekiq/sidekiq/wiki) — проверенный временем стандарт на Redis

## Производительность

- [Active Record Query Guide](https://guides.rubyonrails.org/active_record_querying.html) — как не плодить N+1
- [Bullet](https://github.com/flyerhzm/bullet) — ловит N+1 и лишние запросы в разработке
- [rack-mini-profiler](https://github.com/MiniProfiler/rack-mini-profiler) — профилировщик прямо в браузере
- [Strong Migrations](https://github.com/ankane/strong_migrations) — предохраняет от опасных миграций на проде

## Hotwire — фронтенд без SPA

- [Turbo](https://turbo.hotwired.dev/handbook/introduction) — скорость SPA почти без JavaScript
- [Stimulus](https://stimulus.hotwired.dev/handbook/introduction) — лёгкий JS для оживления готового HTML
- [Hotwire Native](https://native.hotwired.dev/) — нативные мобильные приложения на той же кодовой базе
- [The Turbo Rails Tutorial (hotrails.dev)](https://www.hotrails.dev/) — **лучший практический туториал по Hotwire**

## API и интеграции

- [Rails как API](https://guides.rubyonrails.org/api_app.html) · [то же на русском](https://rusrails.ru/api-app)
- [JSON:API — реализации для Ruby](https://jsonapi.org/implementations/#server-libraries-ruby)
- [GraphQL](https://graphql.org/learn/) · [graphql-ruby](https://graphql-ruby.org/)

## Безопасность

- [Securing Rails Applications](https://guides.rubyonrails.org/security.html) — официальное руководство, обязательно
- [OWASP Top Ten](https://owasp.org/www-project-top-ten/) — карта главных уязвимостей
- [Brakeman](https://brakemanscanner.org/) — статический анализатор безопасности для Rails

## Деплой и CI/CD

Главный сдвиг последних лет — **деплой на свои серверы вместо дорогих PaaS**. Это
центральная идея DHH («No PaaS»), и вокруг неё построен весь стек Rails 8.

- [**Kamal**](https://kamal-deploy.org/) — деплой Docker-контейнеров на любой сервер по SSH, флагман подхода «no-PaaS»
  - [Документация Kamal](https://kamal-deploy.org/docs/installation/) — конфиг, секреты, аксессуары (БД, Redis рядом с приложением)
  - [Репозиторий Kamal](https://github.com/basecamp/kamal) — от Basecamp/37signals
  - 💡 *В Kamal 2+ деплой возможен **без внешнего registry** (Docker Hub/GHCR не обязателен), а секреты берутся прямо из шифрованных credentials Rails.*
- [Solid Cache](https://github.com/rails/solid_cache) · [Solid Cable](https://github.com/rails/solid_cable) — кэш и WebSocket поверх БД, стек Rails 8
- [**`bin/ci`**](https://guides.rubyonrails.org/8_1_release_notes.html) — встроенный в Rails 8.1 CI (`config/ci.rb`), позволяет вести CI без облака — в том же духе «no-PaaS»
- [GitHub Actions](https://docs.github.com/en/actions) — CI/CD пайплайны, если нужен облачный CI
- [Capistrano](https://github.com/capistrano/capistrano) — классический деплой по SSH. *Легаси: для новых проектов выбирай Kamal, актуально лишь для не-контейнерных систем*

## Микросервисы и обмен сообщениями

> Это уже про масштаб. Большинству приложений хватает монолита — сначала освой его.

- [RabbitMQ для Ruby](https://www.rabbitmq.com/tutorials/tutorial-one-ruby) — официальный туториал
- [Karafka](https://github.com/karafka/karafka) — современный фреймворк Kafka для Ruby
- [SOA на Rails + Kafka](https://habr.com/ru/articles/450028/) — введение на русском

---

# 🚀 Уровень 3. IndieHacker / MVP

## Гибридный фронтенд (рецепты Evil Martians)

Когда Hotwire мало и нужен островок React/Vue/Svelte:

- [Turbo Mount](https://evilmartians.com/chronicles/the-art-of-turbo-mount-hotwire-meets-modern-js-frameworks) — точечная интеграция JS-компонентов в Hotwire
- [Inertia.js](https://inertiajs.com/) — SPA-ощущения без написания отдельного API
- [Vite Ruby](https://vite-ruby.netlify.app/) — современная сборка фронтенда для Rails

## Гемы, которые стоит знать

- **[Devise](https://github.com/heartcombo/devise)** — аутентификация (хотя в Rails 8 есть и встроенный генератор)
- **[Pundit](https://github.com/varvet/pundit)** — авторизация по политикам
- **[rails-erd](https://github.com/voormedia/rails-erd)** — ER-диаграммы по моделям
- **[Typelizer](https://github.com/skryukov/typelizer)** — генерация TypeScript-типов из Rails (Evil Martians)
- **[ffaker](https://github.com/ffaker/ffaker)** — генерация тестовых данных
- **[Discourse](https://github.com/discourse/discourse)** — эталонный большой Rails-проект, читать как учебник

---

# 🤖 AI-ассистированная разработка

В 2026-м это уже не модное слово, а часть ремесла — как когда-то Git. И вот честная
причина, почему это особенно важно именно Rails-разработчику: **Rails идеален для ИИ**.
Convention-over-configuration делает структуру проекта предсказуемой, поэтому «первая
догадка» модели о том, где лежит код, почти всегда верна, а Ruby — один из самых
токен-эффективных языков для агентов.

> 🔑 ИИ **не отменяет** принцип этой базы, а усиливает его: модель ошибается там, где
> ты сам не понимаешь доку. **Документация + Практика + ИИ** — но именно в таком
> порядке. Агент — это ускоритель для того, кто знает фундамент, а не замена ему.

## Агенты в терминале

- [**Claude Code**](https://docs.claude.com/en/docs/claude-code/overview) — агент Anthropic прямо в терминале: правит файлы, гоняет тесты, ведёт целые задачи
- [**OpenCode**](https://opencode.ai/) — открытый AI-агент для терминала ([репозиторий](https://github.com/opencode-ai/opencode)): TUI, подключается к **любой** модели — Claude, GPT, Gemini или локальной
- [Qwen Code](https://github.com/QwenLM/qwen-code) — открытый терминальный агент от команды Qwen
- [Cursor](https://cursor.com/) — AI-first IDE (форк VS Code), если предпочитаешь редактор, а не терминал

## Открытые и локальные модели

Если важны приватность, отсутствие облака или экономия — открытые веса догнали проприетарные.

- [**Ollama**](https://ollama.com/) — самый простой способ запустить открытую модель локально; связка **OpenCode + Ollama** даёт полностью локального агента без облака
- [Каталог открытых coding-моделей (2026)](https://kilo.ai/open-source-models) — актуальный обзор
- Заметные на лето 2026: **Qwen3-Coder**, **DeepSeek V4**, **GLM**, **Kimi K2**, **Devstral** — для локального старта обычно советуют Qwen-Coder или Devstral, тяжёлые задачи тянут DeepSeek/GLM/Kimi

## Rails + ИИ: рецепты

- [claude-on-rails](https://github.com/obie/claude-on-rails) — фреймворк для Rails-разработки на Claude Code от Оби Фернандеса
- [rails-instructions](https://github.com/levifig/rails-instructions) — набор «DHH-driven» правил для любого AI-агента (Cursor, Copilot, Claude)
- [thoughtbot: Claude Skill для аудита Rails-кода](https://thoughtbot.com/blog/ai-in-focus:a-new-claude-skill-for-rails-code-audits)
- **MCP** ([Model Context Protocol](https://modelcontextprotocol.io/)) — открытый стандарт Anthropic: подключает агента к БД, гиту, деплою; забирает только нужный контекст и экономит токены

> 💡 Главный конфиг — **`CLAUDE.md`** (или `.cursor/rules`) в корне проекта: туда
> кладёшь соглашения, архитектуру, правила тестов. Это стыкуется с твоим подходом
> вести документацию в Obsidian — одни и те же заметки кормят и тебя, и ИИ.

---

# 📚 Справочник

## Книги

- **Sandi Metz — _Practical Object-Oriented Design in Ruby (POODR)_** — must-read по проектированию объектов
- **thoughtbot — [_Ruby Science_](https://thoughtbot.com/ruby-science/)** — рефакторинг и код-смеллы на живых примерах
- **Роман Пушкин — _Ruby для романтиков_** — мягкий заход в язык для начинающих

## Видео

- [DHH — презентация Rails 8](https://www.youtube.com/watch?v=-cEn_83zRFw) — больше шоу, но заряжает

## Сообщества

- [Rails Discuss](https://discuss.rubyonrails.org/)
- [Hotwire Discussion](https://discuss.hotwired.dev/)

## Избранные статьи

- [Ruby on Rails Design Patterns 101](https://medium.com/@slimbennasrallah_89177/ruby-on-rails-design-patterns-101-d99f43adc2b3)
- [Deploying review apps with Kamal on CI/CD](https://guillaumebriday.fr/deploying-review-apps-automatically-with-kamal-on-ci-cd)
- [Перевод Rails-приложения через OpenAI](https://guillaumebriday.fr/how-i-use-openai-to-translate-my-rails-application-into-multiple-languages)
- [Почему я рекомендую Rails новичкам](https://habr.com/ru/articles/794476/) — Хабр

> Блоги, за которыми стоит следить целиком: [Evil Martians](https://evilmartians.com/chronicles),
> [thoughtbot](https://thoughtbot.com/blog), [GoRails](https://gorails.com/).

## Алгоритмы

- [Грокаем алгоритмы — код примеров](https://github.com/egonSchiele/grokking_algorithms)
- [Sorting Algorithms with Ruby](https://dev.to/daviducolo/sorting-algorithms-with-ruby-4o18)
- [Алгоритмы и структуры данных (видео, Ilya Krukowski)](https://www.youtube.com/playlist?list=PLWlFXymvoaJ-Q8FyOj9SQ3Eoog5Nkv0lI)

## Практика кодом каждый день

Та самая вторая половина формулы. Заведи привычку: одна задача в день — и руки
начинают думать быстрее головы.

- [Codewars](https://codewars.com/) — **рекомендую сильнее всего**, прокачка как игра, есть Ruby
- [Exercism — Ruby track](https://exercism.org/tracks/ruby) — задачи с менторскими ревью, бесплатно
- [LeetCode](https://leetcode.com/) — классика для алгоритмических собеседований
- [Codeforces](https://codeforces.com/) — спортивное программирование
- [Replit](https://replit.com/) — быстро пописать код в браузере без настройки окружения

## Тренажёры продуктивности

- [keybr.com](https://www.keybr.com/) — слепая печать
- **Vim:** [openvim](https://openvim.com/) (тренажёр) · [PacVim](https://github.com/jmoon018/PacVim) (игра)

## Инструменты проектирования и документации

- [dbdiagram.io](https://dbdiagram.io/home/) — схемы БД текстом (DBML), ИИ хорошо генерит этот формат
- [Miro](https://miro.com/) — удобно для схем архитектуры и набросков
- [Draw.io](https://www.drawio.com/) — простой и бесплатный

> 💡 **Веди документацию проекта в [Obsidian](https://obsidian.md/).** Заметки — это
> локальные markdown-файлы, связанные ссылками `[[ ]]` в граф знаний. Так делает и
> рекомендует Андрей Карпаты (Andrej Karpathy): свой «второй мозг» по проекту держишь
> рядом с кодом, а не в чужом облаке.

---

# 🎓 Курсы — если совсем с нуля

> Курсы хороши только для старта. Освоился — переходи к докам выше, дальше растут на них.

**Бесплатные, для начала:**
- [Code Basics — Ruby](https://code-basics.com/ru/languages/ruby) — open-source основы от Hexlet
- [The Odin Project — Full Stack Ruby on Rails](https://www.theodinproject.com/paths/full-stack-ruby-on-rails) — полный бесплатный путь (англ.)
- [Курс Романа Пушкина](https://rubyschool.us/) — бесплатный, слегка устаревший, но добротный

**По подписке, когда нужна практика и видео:**
- [GoRails](https://gorails.com/series) · [Hexlet](https://ru.hexlet.io/courses_ruby)

---

# 💼 Подготовка к собеседованиям

> Отдельная задача: «пройти собес» ≠ «стать профи». Используй после фундамента.

- [Hexlet — вопросы по Rails](https://github.com/Hexlet/ru-interview-questions/blob/main/questions/rails.md)
- [EVRONE Challenge — самопроверка](https://challenge.career.evrone.com/challenge_modules/ruby-on-rails/)
- [Rails Interview Questions (англ., с ответами)](https://github.com/gardeziburhan/rails_interview_questions)
- [Шпаргалка по основам Backend](https://github.com/DEBAGanov/interview_questions/blob/main/1.%20%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B%20Backend-%D1%80%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B8.md)
