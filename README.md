# ПОЛКА

Архив проекта: Telegram Mini App «ПОЛКА» — поиск объявлений по критериям, барахолка, бот-уведомления.

Репозиторий используется как папка для сохранения исходников.

## Что внутри

| Папка / файл | Что это |
|---|---|
| `polka_bot-9-3.py` | весь бэкенд: aiohttp, SQLite, Telegram-бот, API мини-приложения |
| `max_compat.py` | совместимость с MAX-ботом |
| `polka-final/frontend/proto/` | исходники мини-приложения: `template.html`, `build.py`, `adapter.js`, `menu.js`, `payments.js`, `admin.js` |
| `polka-final/frontend/dist/` | то, что раздаётся сервером (после `python3 build.py`) |
| `polka-final/frontend/src/` | React-часть (админка) |
| `collector/` | сборщик объявлений с Авито |
| `tests/` | 43 теста бэкенда |
| `assets/`, `tools/`, `hf-space/` | картинки, вспомогательные скрипты |
| `Dockerfile`, `amvera.yml` | сборка и деплой на Amvera |
| `AUDIT.md` | предрелизный аудит |
| `RUNBOOK.md` | как запускать и чинить |

## Запуск локально

```bash
pip install -r requirements.txt
export BOT_TOKEN=...        # токен бота
export ADMIN_TOKEN=...      # токен админских ручек
python3 polka_bot-9-3.py
```

Мини-приложение собирается так:

```bash
cd polka-final/frontend/proto
python3 build.py
cp index.html ../dist/
```

## Тесты

```bash
for f in tests/test_*.py; do python3 "$f"; done   # 43/43
```

## Важное

- `collector/config.json` в репозиторий не попадает: там токены. Шаблон — `collector/config.example.json`.
- Точка входа мини-приложения — `polka-final/frontend/proto/template.html`, после сборки — `dist/index.html`.
- Меню внизу — `menu.js` (готовый макет заказчика), связка с экранами — `menu-bind.js`.
