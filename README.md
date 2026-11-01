<!-- mcp-name: io.github.basicmachines-co/basic-memory -->
[![MCP Toplist](https://mcptoplist.com/badge/io.github.basicmachines-co%2Fbasic-memory.svg)](https://mcptoplist.com/server/io.github.basicmachines-co%2Fbasic-memory)

[![Лицензия: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Версия PyPI](https://badge.fury.io/py/basic-memory.svg)](https://badge.fury.io/py/basic-memory)
[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Тесты](https://github.com/basicmachines-co/basic-memory/workflows/Tests/badge.svg)](https://github.com/basicmachines-co/basic-memory/actions)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
![](https://badge.mcpx.dev?type=server 'MCP Server')
![](https://badge.mcpx.dev?type=dev 'MCP Dev')
[![Спросить DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/basicmachines-co/basic-memory)

<a name="skip-the-install--try-basic-memory-in-the-cloud"></a>
## Попробуйте Basic Memory в облаке без установки

Подключите Claude, Codex или Cursor за 30 секунд — без Python, JSON и терминала.
**$15 в месяц с фиксированной ценой на весь срок подписки** ($12,50 в месяц при
оплате за год). Бесплатный пробный период — 7 дней; если сервис не подойдёт,
подписку можно отменить до окончания седьмого дня. Это цена бета-версии: при
оформлении сейчас тариф не повысится. Для пользователей проектов с открытым кодом
промокод `BMFOSS` даёт дополнительную скидку 20% на три месяца.

[Начать бесплатный пробный период →](https://basicmemory.com?utm_source=github&utm_medium=referral&utm_campaign=readme&utm_content=banner)

<a name="basic-memory-teams-is-now-available"></a>
### Basic Memory Teams уже доступен!

Создайте единое облачное рабочее пространство для команды. Знания не останутся у
одного человека: всё, что записывает участник команды, сразу доступно остальным и
их ИИ-помощникам. Редактируйте заметки вместе в реальном времени, передавайте
задачи людям и агентам и создавайте общую связанную базу знаний вместо разрозненных
копий. Тариф тот же: начните с одного пользователя и добавляйте остальных по мере
необходимости.

---

# Basic Memory

<a name="your-ai-never-forgets-again"></a>
### Ваш ИИ больше ничего не забудет.

Продолжайте работу с того места, где остановились, — в Claude, Codex, Cursor,
ChatGPT или любом другом клиенте, поддерживающем [MCP](https://modelcontextprotocol.io).
Ваши знания хранятся в Markdown-файлах, которые вы и ваш ИИ можете читать,
редактировать и искать.

- **Локальное хранение.** Обычные текстовые файлы на вашем диске.
- **Двусторонняя работа.** ИИ и люди работают с одними файлами, а синхронизация
  поддерживает их согласованность.
- **Граф знаний.** Наблюдения и вики-ссылки связывают сведения и формируют контекст.
- **Семантический поиск.** Находите заметки по смыслу и ключевым словам; при
  необходимости используйте повторное ранжирование кросс-энкодером для улучшения
  векторного и гибридного поиска.
- **Поддержка MCP.** Работает с основными ИИ-клиентами и средами разработки.
- **Постепенное обнаружение инструментов.** Каждый инструмент снабжён подсказками
  о его поведении (только чтение, разрушительное действие, идемпотентность), чтобы
  агент выбирал нужный инструмент без лишних проб и затрат контекста.
- **Облако по желанию.** Синхронизируйте данные между устройствами, когда это нужно.

<a name="get-started"></a>
## С чего начать

Выберите подходящий вариант. В обоих случаях используется один продукт и одни и
те же файлы Markdown.

<table>
<tr>
<th width="50%">☁️ &nbsp; Облако</th>
<th width="50%">💻 &nbsp; Локальная установка</th>
</tr>
<tr>
<td valign="top">

**30 секунд.** Зарегистрируйтесь и подключите ИИ-клиент.

- Работает в любом браузере
- Доступен на телефоне, в браузере и на компьютере
- Встроенная синхронизация между устройствами
- Размещение, резервные копии и снимки предоставляет сервис

**$15 в месяц с фиксированной ценой** · 7 дней бесплатно · отмена в любой момент

[**Начать бесплатный пробный период →**](https://basicmemory.com?utm_source=github&utm_medium=referral&utm_campaign=readme&utm_content=quickstart)

</td>
<td valign="top">

**2 минуты.** Установите программу, настройте ИИ-клиент и запускайте.

- Бесплатно (AGPL-3.0)
- Все данные на вашем диске
- Подходит для изолированной сети
- Требуется Python через [`uv`](https://docs.astral.sh/uv/)

```bash
uv tool install basic-memory --prerelease=allow
```

Флаг `--prerelease=allow` обязателен: Basic Memory 0.23 зависит от предварительной
версии FastMCP 4, а `uv` разрешает предварительные версии транзитивных зависимостей
только при явном указании этого флага. Без него будет установлена более старая
версия. Используйте тот же флаг в приведённых ниже командах `uvx` и `uv tool upgrade`.

Для развёртывания с Postgres, где семантические векторы хранятся в Milvus,
установите официальный дополнительный пакет:

```bash
uv tool install "basic-memory[milvus]" --prerelease=allow
```

[**Настроить клиент ↓**](#connect-your-ai-client)

</td>
</tr>
</table>

<a name="what-people-are-saying"></a>
## Отзывы пользователей

> Basic Memory полностью изменил моё отношение к языковым моделям. Благодаря этой
> интеграции я перешёл с GPT и Gemini исключительно на Claude и Claude Code и
> полностью перестраиваю процессы нашей компании вокруг Basic Memory.
>
> — **Alex**, TrainerDay

> Basic Memory — недостающий вау-эффект ИИ-чатов. Теперь я не представляю Claude
> или Claude Code без него.
>
> — **Caleb**, Caleb Picker Consulting

> Я больше не пишу код без Basic Memory. Это экономит много времени: можно
> обращаться к проектам, которые сейчас не активны, и вести журнал находок и
> полезных приёмов.
>
> — **@groksrc**, разработчик

Подробнее на [basicmemory.com](https://basicmemory.com?utm_source=github&utm_medium=referral&utm_campaign=readme).

## Basic Memory Cloud

Облачная версия Basic Memory: тот же продукт, те же Markdown-файлы и инструменты
MCP. Сервис размещает базу данных, выполняет синхронизацию и предоставляет доступ
с телефона.

<a name="what-you-get"></a>
### Что входит

- **Единая база на всех устройствах.** Граф знаний доступен в браузере, на телефоне
  и компьютере без копирования между устройствами.
- **Подключение MCP-клиентов.** Claude Desktop, Claude Code, Codex, Cursor,
  ChatGPT (пользовательские GPT) и VS Code подключаются из веб-приложения.
- **Двусторонняя синхронизация с локальными файлами.** Измените заметку на телефоне —
  и она появится в Obsidian на компьютере. Используется rclone с разрешением конфликтов.
- **Снимки и резервные копии.** Восстановление на выбранный момент и просмотр истории.
- **Доступность данных.** Заметки остаются обычным Markdown. Их можно в любой момент
  экспортировать локально с тем же форматом и вики-ссылками, а подписку — отменить.

Используются WorkOS AuthKit, Neon Postgres и Tigris S3.

<a name="pricing"></a>
### Стоимость

**$15 в месяц с фиксацией цены на весь срок подписки** (обычная цена — $19).
При оформлении в период бета-тестирования цена сохраняется, пока действует
подписка. Один тариф без уровней и неожиданных доплат: неограниченное число
заметок и проектов и все функции.

- 7 дней бесплатно; подписку можно отменить до окончания пробного периода.
- После него подписку также можно отменить в любой момент и экспортировать заметки.
- Промокод `BMFOSS` даёт пользователям проектов с открытым кодом дополнительную
  скидку 20% на три месяца (около $11,40 в месяц).

[**Начать бесплатный пробный период →**](https://basicmemory.com?utm_source=github&utm_medium=referral&utm_campaign=readme&utm_content=cloud-section)

<a name="cloud-vs-local"></a>
## Облачная и локальная версии

|  | Облако | Локальная установка |
|---|---|---|
| **Время настройки** | 30 секунд | 2 минуты (требуется Python) |
| **Стоимость** | $15 в месяц с фиксированной ценой, пробный период 7 дней | Бесплатно |
| **Хранение** | На серверах сервиса (Tigris S3) | На вашем диске |
| **Синхронизация устройств** | Встроена | Вручную: Git, Syncthing и др. |
| **Доступ с телефона** | Да, через веб и приложение | Нет |
| **Работа в изолированной сети** | Нет | Да |
| **Данные остаются вашими** | Да, можно экспортировать | Да, они уже у вас |
| **Исходный код** | AGPL-3.0 | AGPL-3.0 |
| **Снимки и резервные копии** | Встроены | Настраиваются самостоятельно |

Оба варианта используют один движок с открытым кодом и одни и те же файлы
Markdown. При необходимости можно перейти с одного варианта на другой.

<a name="works-with-the-tools-you-already-use"></a>
## Работа с привычными инструментами

| Клиент | Транспорт | Примечание |
|---|---|---|
| Облачное веб-приложение | https | Вход на basicmemory.com, установка не требуется |
| [Claude Desktop](#claude-desktop) | stdio/https | macOS / Windows / Linux |
| [Claude Code](#claude-code) | stdio/https | `claude mcp add` |
| [Codex](#codex-cli) | stdio/https | Агент OpenAI для работы с кодом |
| [Cursor](#cursor) | stdio/https | `.cursor/mcp.json` |
| [VS Code](#vs-code) | stdio/https | Встроенная поддержка MCP |
| [ChatGPT](#chatgpt) | https | Действия пользовательских GPT (`search` / `fetch`) |
| [Obsidian](#obsidian) | — | Напрямую читает и записывает те же Markdown-файлы |
| Другие MCP-клиенты | stdio/https | Подойдёт любой совместимый с MCP клиент |

<a name="official-agent-packages"></a>
## Официальные пакеты для агентов

В этом репозитории также хранятся официальные пакеты Basic Memory для разных сред:
основной пакет Python, плагин Claude Code, общие навыки, плагины Hermes и OpenClaw.
Все они выпускаются из одного дерева исходного кода.

Для проверки всех пакетов из корня репозитория:

```bash
just package-check
```

Для проверки отдельных пакетов доступны команды:

```bash
just package-check-claude-code
just package-check-skills
just package-check-hermes
just package-check-openclaw
```

<a name="claude-code-plugin"></a>
### Плагин Claude Code

Плагин соединяет рабочую память Claude с Basic Memory: предоставляет сводки в
начале сессии, контрольные точки перед сжатием контекста, включаемый по желанию
режим сохранения и команды `/basic-memory:bm-setup` · `:remember` · `:share` · `:status`.

**Сначала подключите MCP-сервер Basic Memory** — см. раздел [«Подключение
ИИ-клиента»](#connect-your-ai-client). Хуки и навыки плагина обращаются к серверу,
поэтому он обязателен. Затем установите плагин:

```bash
bm install claude-code
```

Команда регистрирует каталог и устанавливает плагин через Claude Code. Добавьте
`--scope project`, чтобы объявить оба компонента в настройках репозитория для
команды, или `--dry-run`, чтобы увидеть команды `claude plugin` без их выполнения.

Исходный код: [`plugins/claude-code`](plugins/claude-code).

<a name="shared-skills"></a>
### Общие навыки

Независимые от среды файлы `SKILL.md` находятся в [`skills/`](skills). Если ваш
Skills CLI поддерживает загрузку из подкаталога репозитория:

```bash
npx skills add basicmachines-co/basic-memory/skills -g
```

Для Claude и ChatGPT загрузите `basic-memory.zip` или `basic-memory-chatgpt.zip`
из выпуска [`skills-latest`](https://github.com/basicmachines-co/basic-memory/releases/tag/skills-latest);
см. [`skills/README.md`](skills/README.md#installation).

Если установленный Skills CLI не поддерживает этот источник, обновите CLI или
скопируйте каталоги `memory-*` из `skills/` в каталог навыков своего агента.

### Hermes

Плагин Hermes находится в [`integrations/hermes`](integrations/hermes):

```bash
hermes plugins install basicmachines-co/basic-memory/integrations/hermes
```

Hermes не устанавливает зависимости Python для плагинов, поэтому дополнительно
установите пакет `mcp` в виртуальное окружение Hermes. Инструкции и поддерживаемые
версии приведены в [README плагина](integrations/hermes/README.md#install).

### OpenClaw

Плагин OpenClaw выпускается из [`integrations/openclaw`](integrations/openclaw):

```bash
openclaw plugins install @basicmemory/openclaw-basic-memory
```

<a name="pick-up-where-you-left-off"></a>
## Продолжайте с того места, где остановились

https://github.com/user-attachments/assets/a55d8238-8dd0-454a-be4c-8860dbbd0ddc

<a name="connect-your-ai-client"></a>
## Подключение ИИ-клиента

Если вы выбрали [облачную версию](#get-started), веб-приложение поможет подключить
клиент. Примеры ниже предназначены для локальной установки.

### Claude Desktop

Отредактируйте `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "basic-memory": {
      "command": "uvx",
      "args": ["--prerelease=allow", "basic-memory", "mcp"]
    }
  }
}
```

Перезапустите Claude Desktop. По умолчанию заметки хранятся в `~/basic-memory`.

<details>
<summary><b>Claude Code, Codex CLI, Cursor, VS Code, ChatGPT, Obsidian</b></summary>

### Claude Code

```bash
claude mcp add basic-memory -- uvx --prerelease=allow basic-memory mcp
```

Чтобы использовать сводки сессий, контрольные точки перед сжатием контекста и
команды `/basic-memory:*`, дополнительно установите [плагин Claude Code](#claude-code-plugin).

### Codex CLI

Добавьте в `~/.codex/config.toml`:

```toml
[mcp_servers.basic-memory]
command = "uvx"
args = ["--prerelease=allow", "basic-memory", "mcp"]
```

Можно оставить стандартный порядок подтверждения MCP в Codex или предварительно
разрешить подходящие инструменты Basic Memory, добавив в ту же таблицу настройку,
действующую только для этого сервера:

```toml
[mcp_servers.basic-memory]
command = "uvx"
args = ["--prerelease=allow", "basic-memory", "mcp"]
default_tools_approval_mode = "approve"
```

Эта настройка не отключает подтверждения Codex глобально и не расширяет доступ
сервера к проектам Basic Memory. Codex по-прежнему требует подтверждения для
инструментов с пометкой о разрушительном действии, включая запись, редактирование
и удаление в Basic Memory. Если установлен плагин Basic Memory для Codex,
используйте [настройку для плагина](plugins/codex/README.md#mcp-approvals).

### Cursor

Добавьте в `.cursor/mcp.json` для проекта или `~/.cursor/mcp.json` глобально:

```json
{
  "mcpServers": {
    "basic-memory": {
      "command": "uvx",
      "args": ["--prerelease=allow", "basic-memory", "mcp"]
    }
  }
}
```

### VS Code

Добавьте в пользовательские настройки JSON:

```json
{
  "mcp": {
    "servers": {
      "basic-memory": {
        "command": "uvx",
        "args": ["--prerelease=allow", "basic-memory", "mcp"]
      }
    }
  }
}
```

### ChatGPT

Basic Memory предоставляет совместимые с OpenAI инструменты `search` и `fetch`
для действий пользовательских GPT. См. [руководство по интеграции с ChatGPT](https://docs.basicmemory.com/integrations/chatgpt/?utm_source=github&utm_medium=referral&utm_campaign=readme).

### Obsidian

Дополнительная настройка не требуется. Укажите в Obsidian каталог `~/basic-memory`
или папку проекта: в представлении графа появятся те же вики-ссылки, frontmatter и
Markdown, которые записывает ИИ. Можно редактировать файлы с любой стороны —
синхронизация согласует изменения.

</details>

Попробуйте запрос:

```text
«Создай заметку о решениях по архитектуре нашего проекта».
«Найди в моих заметках информацию об авторизации JWT».
«Над чем я работал на этой неделе?»
```

<a name="whats-new"></a>
## Что нового

- **Автоматические обновления.** При установке через `uv tool` и Homebrew Basic Memory
  обновляется автоматически; команда `bm update` запускает проверку вручную.
- **Семантический векторный поиск.** Поиск по смыслу и ключевым словам: гибридное
  ранжирование по полному тексту и векторам FastEmbed в SQLite или Postgres.
- **Необязательное повторное ранжирование.** Уточнение лучших векторных и гибридных
  результатов локальным кросс-энкодером FastEmbed или поставщиком через LiteLLM.
- **Система схем.** Определение, проверка и сравнение структуры базы знаний с помощью
  `bm_schema(command="infer")`, `bm_schema(command="validate")` и
  `bm_schema(command="diff")`.
- **Маршрутизация в облако по проектам.** Отдельные проекты могут работать через
  облако по API-ключу (`bm project set-cloud`), остальные остаются локальными.
- **Явные операции с заметками.** `bm_edit` обновляет существующие заметки; `bm_write`
  создаёт заметки и защищает от случайной перезаписи.
- **Более подробные результаты поиска.** Модель получает текст найденных фрагментов
  и контекст, а не только список совпадений.
- **FastMCP 3.0 и аннотации инструментов.** Подсказки MCP (`readOnlyHint`,
  `destructiveHint`, `idempotentHint`, `openWorldHint`) помогают агентам обнаруживать
  возможности во время работы без лишних догадок и расхода контекста.
- **Обновлённый CLI.** Вывод `--json` для скриптов, команды с учётом рабочего
  пространства и панель проектов в стиле htop.

Полный список изменений с v0.18 до v0.20 — в [CHANGELOG](CHANGELOG.md).

<a name="optional-cross-encoder-reranking"></a>
## Необязательное повторное ранжирование кросс-энкодером

После векторного или гибридного поиска повторное ранжирование дополнительно
оценивает релевантность результатов. По умолчанию оно выключено: этот этап
увеличивает время обработки, а для локального поставщика при первом запуске
требуется скачать модель. Порядок результатов текстового поиска, поиска по
заголовку и постоянной ссылке не меняется.

Чтобы включить стандартный локальный ранжировщик FastEmbed:

```bash
export BASIC_MEMORY_RERANKER_ENABLED=true
```

Модель по умолчанию — `jinaai/jina-reranker-v1-tiny-en`. Чтобы использовать
внешний ранжировщик через LiteLLM:

```bash
export BASIC_MEMORY_RERANKER_ENABLED=true
export BASIC_MEMORY_RERANKER_PROVIDER=litellm
export BASIC_MEMORY_RERANKER_MODEL=cohere/rerank-v3.5
export COHERE_API_KEY=...
```

При неверной конфигурации функция сразу сообщает об ошибке; при сбое включённого
поставщика она не переключается незаметно на исходный порядок результатов. Настройка
поставщиков, параметры, пагинация и поведение при ошибках описаны в
[руководстве по семантическому поиску](docs/semantic-search.md#cross-encoder-reranking).

<a name="why-basic-memory"></a>
## Зачем нужен Basic Memory

Большинство разговоров с языковыми моделями недолговечны: вы задаёте вопрос,
получаете ответ, а затем контекст забывается. У распространённых способов хранения
есть ограничения:

- **История чатов** сохраняет разговоры, но не превращает их в структурированные знания.
- **RAG** позволяет модели искать в документах, но не записывать изменения обратно.
- **Векторные базы** требуют сложной инфраструктуры и часто размещаются в чужом облаке.
- **Графам знаний** нужны специальные инструменты для сопровождения.

Basic Memory использует **структурированные Markdown-файлы**, которые могут читать
и редактировать и человек, и языковая модель.

- Знания остаются в обычных файлах под вашим контролем.
- Человек и ИИ работают с одними и теми же файлами.
- Используется привычный Markdown с семантическими конструкциями.
- Модель может переходить по связям графа.
- Подходят привычные редакторы: Obsidian, VS Code и другие.
- Достаточно файлов и локального индекса SQLite; отдельный сервер не требуется.

<a name="how-it-works"></a>
## Как это работает

Представим обычный разговор о кофе:

> Я пробовал разные способы заваривания. Пуровер даёт более чистый вкус, чем
> френч-пресс, температура около 205 °F подходит лучше всего, а свежий помол
> сильно меняет результат.

Попросите модель сохранить информацию:

> «Создай заметку о способах заваривания кофе».

В каталоге проекта сразу появится Markdown-файл:

```markdown
---
title: Coffee Brewing Methods
permalink: coffee-brewing-methods
tags: [coffee, brewing]
---

# Coffee Brewing Methods

## Observations
- [method] Pour over highlights subtle flavors over body
- [technique] Water at 205°F (96°C) extracts optimal compounds
- [principle] Freshly ground beans preserve aromatics

## Relations
- relates_to [[Coffee Bean Origins]]
- requires [[Proper Grinding Technique]]
- affects [[Flavor Extraction]]
```

В следующей сессии модель продолжит разговор: перейдёт по связям, найдёт уже
сохранённые сведения об эфиопском кофе и жерновых кофемолках и учтёт их. Те же
файлы видны в Obsidian или другом редакторе. Если изменить их вручную, ИИ тоже
увидит изменения.

Люди редактируют Markdown, модели читают и записывают через MCP, синхронизация
поддерживает согласованность, а источником данных остаются ваши файлы.

<a name="the-markdown-format"></a>
## Формат Markdown

Каждый файл — это сущность (`Entity`). У сущностей есть наблюдения (`Observations`:
факты о них) и отношения (`Relations`: связи с другими сущностями). Так устроен
основной формат.

### Frontmatter

```markdown
---
title: <Entity title>
type: note
permalink: <uri-slug>
tags: [optional, list]
---
```

<a name="observations"></a>
### Наблюдения

Факты о сущности: категории указываются в `[квадратных скобках]`, теги — через
`#`, необязательный контекст — в круглых скобках.

```markdown
- [method] Pour over highlights subtle flavors
- [tip] Grind medium-fine for V60 #brewing
- [fact] Lighter roasts contain more caffeine than dark
- [resource] James Hoffmann's V60 technique on YouTube
- [question] How does temperature affect compound extraction?
```

<a name="relations"></a>
### Отношения

Вики-ссылки, образующие граф. Тип отношения записывается одним словом; типы из
нескольких слов заключаются в кавычки.

```markdown
- pairs_well_with [[Chocolate Desserts]]
- grown_in [[Ethiopia]]
- requires [[Burr Grinder]]
- "pairs well with" [[Dark Chocolate]]
```

Ссылка без указанного типа `- [[Target]]` и ссылка в тексте
`- Worth checking out [[Target]]` индексируются как `links_to`. Полное описание —
в [документации](https://docs.basicmemory.com/concepts/knowledge-format?utm_source=github&utm_medium=referral&utm_campaign=readme).

<a name="mcp-tools"></a>
## Инструменты MCP

Basic Memory предоставляет эти инструменты любому MCP-клиенту. Каждый инструмент
имеет подсказки о поведении MCP — только чтение, разрушительное действие,
идемпотентность и взаимодействие с внешним миром, — чтобы агент мог выбрать
подходящий без проб и ошибок:

- **Содержимое:** `bm_write`, `bm_read`, `bm_edit`, `bm_move`, `bm_delete`.
- **Поиск и обзор:** `bm_search`, `bm_list`, `bm_find`.
- **Граф знаний:** `bm_context`.
- **Проекты:** `bm_project(command="list" | "create" | "recent")`;
  `bm_project_delete` предоставляется отдельно и требует включения на сервере.
- **Схема:** `bm_schema(command="validate" | "infer" | "diff")`.
- **Справка:** `bm_man`.
- **Совместимость и диагностика:** `search`, `fetch`, `basic_memory_diagnostics`.

Большинство инструментов по умолчанию возвращают текст, а `bm_context` — JSON.
Для структурированного ответа передайте `output_format="json"`. Инструменты,
работающие в пределах проекта, принимают в `project` имя, `workspace/project`
или внешний UUID. Актуальное описание установленного инструмента можно получить
через `bm_man(page="bm-search(3)")`; см. также [руководство по инструментам](docs/ai-assistant-guide-extended.md).
Названия команд CLI остаются прежними.

<a name="cli-essentials"></a>
## Основные команды CLI

```bash
# Проекты
basic-memory project list
basic-memory project add research ~/research
basic-memory project set-cloud research   # направить через облако
basic-memory project set-local research   # вернуть локальную работу

# Конфигурация
basic-memory config list                        # все настройки, действующие значения и переопределения
basic-memory config set cli_output_style plain  # проверка по модели конфигурации
basic-memory config unset cli_output_style      # вернуть значение по умолчанию

# Состояние и обслуживание
basic-memory status
basic-memory doctor              # проблемы проектов и команды исправления
basic-memory tool edit-note ...  # доступ к инструментам MCP через CLI
basic-memory update              # проверить и установить обновления

# Импорт
basic-memory import claude conversations
basic-memory import chatgpt
basic-memory import memory-json
```

В смешанном режиме флаги маршрутизации `--local` и `--cloud` принудительно
выбирают локальное или облачное направление. Полный справочник CLI приведён в
[документации](https://docs.basicmemory.com/reference/cli-reference?utm_source=github&utm_medium=referral&utm_campaign=readme).

<a name="auto-updates"></a>
## Автоматические обновления

При установке CLI по умолчанию проверяет обновления каждые 24 часа и применяет их
без вывода сообщений, чтобы MCP-сервер продолжал отвечать.

- Поддерживаются установки через `uv tool` и Homebrew.
- Для `uvx` проверка пропускается: временной средой управляет uv.
- Вручную: `bm update` проверяет и устанавливает обновления; `bm update --check`
  только проверяет их наличие.

Отключить обновления можно в `~/.basic-memory/config.json`:

```json
{ "auto_update": false }
```

<a name="telemetry"></a>
## Телеметрия

Собирается минимальный набор анонимных событий, позволяющих понять, как пользователи
переходят от CLI к облачной версии.

**Что собирается:** показы предложений облачной версии, попытки входа в облако и
их результаты, события отключения предложений.

**Что не собирается:** содержимое файлов, заголовки заметок, данные базы знаний,
личные данные, IP-адреса и сведения о каждой отдельной команде или инструменте.

События отправляются в экземпляр [Umami Cloud](https://umami.is) проекта с открытым
кодом, ориентированного на конфиденциальность. Отправка выполняется в фоновом
потоке и не блокирует CLI.

Чтобы отключить сбор:

```bash
export BASIC_MEMORY_NO_PROMOS=1
```

Эта настройка отключает предложения облачной версии и всю телеметрию.

<a name="logging"></a>
## Журналирование

Basic Memory использует [Loguru](https://github.com/Delgan/loguru). Настройки по
умолчанию зависят от способа запуска:

| Компонент | По умолчанию | Причина |
|---|---|---|
| Команды CLI | Только файл | Не мешает выводу команды |
| MCP-сервер | Только файл | Вывод в stdout нарушил бы JSON-RPC |
| API-сервер | Файл локально или stdout в облаке | Docker и облако используют stdout |

Файл журнала: `~/.basic-memory/basic-memory.log`. Ротация при размере 10 МБ,
хранение — 10 дней.

<a name="environment-variables"></a>
### Переменные окружения

| Переменная | По умолчанию | Назначение |
|---|---|---|
| `BASIC_MEMORY_LOG_LEVEL` | `INFO` | DEBUG / INFO / WARNING / ERROR |
| `BASIC_MEMORY_CLOUD_MODE` | `false` | Запись журналов API в stdout со структурированным контекстом |
| `BASIC_MEMORY_FORCE_LOCAL` | `false` | Принудительная локальная маршрутизация API |
| `BASIC_MEMORY_FORCE_CLOUD` | `false` | Принудительная облачная маршрутизация API |
| `BASIC_MEMORY_EXPLICIT_ROUTING` | `false` | Отметить выбор маршрута как явный |
| `BASIC_MEMORY_ENV` | `dev` | Для тестового режима установить `test`; вывод только в stderr |
| `BASIC_MEMORY_NO_PROMOS` | `false` | Отключить предложения облачной версии и телеметрию |
| `BASIC_MEMORY_IMPORT_UPLOAD_MAX_BYTES` | `104857600` | Максимальный размер загружаемого импорта |

```bash
BASIC_MEMORY_LOG_LEVEL=DEBUG basic-memory reindex
tail -f ~/.basic-memory/basic-memory.log
```

<a name="development"></a>
## Разработка

Basic Memory поддерживает SQLite (по умолчанию, быстро, Docker не требуется) и
Postgres (через testcontainers; требуется Docker).

```bash
just install          # установка с зависимостями для разработки
just test-sqlite      # все тесты для SQLite
just test-postgres    # все тесты для Postgres (testcontainers)
just test             # обе базы данных
just fast-check       # исправление, форматирование, проверка типов и затронутые тесты
just doctor           # проверка согласованности файлов и БД с временной конфигурацией
just package-check    # проверка пакетов Claude Code, навыков, Hermes и OpenClaw
just lint
just typecheck        # Pyright — основная проверка
just typecheck-ty     # ty — дополнительная проверка
just format
just check            # все проверки качества
just migration "msg"  # новая миграция Alembic
```

Для тестов используются маркеры pytest: `windows`, `benchmark`, `smoke`. Полный
список приведён в [justfile](justfile).

Вклад в проект приветствуется — см. [CONTRIBUTING.md](CONTRIBUTING.md).

<a name="license"></a>
## Лицензия

[AGPL-3.0](LICENSE).

Создано с ♥️ командой [Basic Machines](https://basicmachines.co?utm_source=github&utm_medium=referral&utm_campaign=readme)
