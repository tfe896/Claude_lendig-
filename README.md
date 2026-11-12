# Landing playbook: правила й інструменти для лендінгів AIN

Спільний репозиторій для всіх лендінгів (мудборд → Figma → Webflow → анімації → кінцевий блок). Тут **немає даних жодного клієнта**: лише правила роботи, інструменти й шаблони. Кожен клієнт живе у своїй папці `<client>-landing/` (або в окремому репозиторії), створеній із шаблону.

## Що тут
| Файл / папка | Призначення |
|---|---|
| `CLAUDE.md` | головні принципи й етапи по порядку; Claude Code читає його на початку кожної сесії |
| `shared/README.md` | швидкий шлях коду від джерела до Webflow |
| `shared/webflow-tools/` | `build_files.py` (збірка двох файлів для Webflow Assets), `wfup.py` (завантаження в Assets) |
| `shared/qa/` | Playwright-перевірки: мобільна версія, заставка, паралакс, жива сторінка |
| `shared/ain-footer/` | кінцевий блок усіх лендінгів: титри, «Читайте також», футер AIN (змінюються лише картки в `cards.json`) |
| `shared/client-template/`, `shared/new_client.py` | стартова структура нового клієнта |
| `shared/templates/TEAM-GUIDE.md` | шаблон інструкції для команди (що правити у Webflow без коду) |

## Старт нового клієнта
```bash
python3 shared/new_client.py <name> <prefix> "<Назва проєкту>"
```
Створить `<name>-landing/` з `CLAUDE.md` і `README.md` клієнта та заготовкою `site/js/<name>.js` + `site/css/anim.css` за нашим контрактом. Далі етапи з `CLAUDE.md`.

## Що налаштувати в новому середовищі Claude Code (цього немає в репозиторії)
1. **Підключення:** Webflow MCP, Figma (MCP і/або токен для REST API лише з читанням, який вводять лише через форму `request_credential`, ніколи в чат).
2. **Дозволені хости середовища:** `api.figma.com`, `figma-alpha-api.s3.us-west-2.amazonaws.com`, `s3-alpha-sig.figma.com`, `drive.google.com`, `drive.usercontent.google.com`, `lh3.googleusercontent.com`, `cdn.prod.website-files.com`, а також адреса сайту Webflow, який перевіряємо вживу (`<site>.webflow.io`).
3. **Playwright і Chromium** у середовищі вже є, нічого ставити не треба. `npx terser` потрібен збірці (підтягується сам).
4. **Ліцензійні шрифти** клієнтів у репозиторій не комітимо (папка `fonts/` у `.gitignore`).
5. Репозиторій краще **приватний**: у проєктах клієнтів лежать їхні матеріали.

## Приклади повних проєктів
Mazda × Співпраця (макет у Figma, сторінка Webflow, версії коду, кінцевий блок) і Godlike × AIN лежать у репозиторії `tfe896/ain_hata` (папки `mazda-landing/`, `godlike-landing/`). Це зразки, як виглядає завершений клієнт: їхні `CLAUDE.md` і `README.md` показують, що саме записувати.
