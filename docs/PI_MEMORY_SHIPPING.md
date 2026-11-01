<a name="pi-memory-package-shipping-checklist"></a>
# Контрольный список выпуска пакета Pi memory

<a name="package-contents"></a>
## Состав пакета

Пакет Pi находится в `integrations/pi/` и предназначен для публикации как
`@basicmemory/pi-basic-memory`.

В пакет входят:

- метаданные пакета Pi в `package.json` (`pi.extensions`, `pi.skills`, ключевое
  слово `pi-package`, настройки публичной публикации в npm);
- исходный код расширения TypeScript в `extensions/`;
- активный навык с поддержкой Pi в `skills/basic-memory-pi/`;
- прилагаемые канонические справочные материалы Basic Memory в
  `skill-references/*/REFERENCE.md`;
- документация по интеграции навыков в `SKILLS.md`;
- пользовательский README в `README.md`;
- лицензия AGPL-3.0-or-later.

`pi-mcp-adapter` не входит в пакет: для режима MCP пользователь устанавливает эту
необязательную зависимость отдельно:

```bash
pi install npm:pi-mcp-adapter
```

<a name="maintainer-checks"></a>
## Проверки сопровождающего

Из корня монорепозитория:

```bash
just package-check-pi
```

Команда запускает:

1. `npm ci --ignore-scripts`
2. `npm run fetch-skills`
3. `npm run check-types`
4. `npm test`
5. `npm pack --dry-run`

Перед созданием или слиянием PR запустите расширенные проверки пакетов:

```bash
just package-check
```

При изменении механизмов выпуска или поведения CLI запустите проверки Python:

```bash
just fast-check
```

<a name="skill-refresh"></a>
## Обновление навыков

Pi включает набор навыков для продолжения работы, скопированных из канонических
навыков Basic Memory верхнего уровня:

- `memory-notes`
- `memory-capture`
- `memory-continue`
- `memory-tasks`

Для обновления:

```bash
cd integrations/pi
npm run fetch-skills
```

Сгенерированный `skill-references/manifest.json` следует включить в коммит вместе
с файлами `REFERENCE.md`, входящими в пакет.

<a name="manual-e2e-before-shipping"></a>
## Ручная сквозная проверка перед выпуском

Используйте изолированное временное окружение. Не изменяйте действующие проекты
Basic Memory или рабочую конфигурацию Pi.

Минимальные сценарии:

1. Сохранение через CLI в Basic Memory, затем извлечение через CLI в новой сессии Pi.
2. Извлечение заметки, записанной через CLI, в режиме MCP через `pi-mcp-adapter`.
3. Запись через `bm_write` адаптера MCP и последующее нахождение заметки через
   извлечение или поиск CLI.
4. В режиме MCP отсутствие адаптера вызывает предупреждение, но Pi остаётся доступным.
5. Отсутствующий или некорректный `bmPath` вызывает видимое сообщение об ошибке
   сохранения или извлечения; система не утверждает, что данные сохранены.

Последние результаты ручной проверки: `docs/PI_MEMORY_E2E_RESULTS.md`.

<a name="release-wiring"></a>
## Механизм выпуска

`just set-version ... --scope packages` обновляет:

- `integrations/pi/package.json`
- `integrations/pi/package-lock.json`

Сценарии стабильного и бета-выпуска включают эти файлы в коммит обновления версии.

<a name="publishing"></a>
## Публикация

Процесс выпуска пакета Python сейчас публикует артефакты PyPI, npm-пакет OpenClaw,
выпуск GitHub и Homebrew. Для автоматической публикации Pi в npm ещё требуется
настроить workflow.

До объявления пакета готовым к выпуску остаётся:

- Добавить публикацию `integrations/pi` в npm через GitHub Actions с той же политикой
  версий и тегов, что у OpenClaw.
- Решить, публиковать ли Pi только по стабильным тегам или также по бета-тегам.
- Добавить страницу интеграции Pi на docs.basicmemory.com в репозитории документации.
- При желании добавить метаданные галереи пакетов (`image` или `video`) до публичного
  объявления.
