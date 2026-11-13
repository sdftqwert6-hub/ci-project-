# MyWebsite — CI/CD practice project

Учебный адаптивный сайт-портфолио для практической работы по анализу и настройке CI/CD.

## Структура проекта

```text
ci-cd-website/
├── index.html
├── style.css
├── script.js
├── images/
│   └── creative-work.svg
├── .github/
│   └── workflows/
│       └── ci.yml
└── README.md
```

## Запуск локально

Откройте `index.html` в браузере или запустите проект через расширение Live Server в Visual Studio Code.

## CI — автоматическая проверка

Workflow `Website CI` запускается при отправке изменений (`push`) в ветку `main`. Он:
1. получает файлы репозитория с помощью `actions/checkout@v4`;
2. проверяет наличие `index.html`, `style.css` и `script.js`;
3. завершает запуск успешно, если все три файла существуют.

### Проверка ошибки

Чтобы проверить обработку ошибок, временно переименуйте `style.css`, например в `style-temp.css`, и отправьте изменения. Шаг `Check project structure` завершится ошибкой, потому что команда `test -f style.css` не найдёт файл. Верните имя `style.css` и отправьте исправление — workflow должен пройти успешно.

## Публикация через GitHub Pages

В репозитории откройте **Settings → Pages**. В разделе Build and deployment выберите **Deploy from a branch**, ветку **main** и папку **/(root)**, затем нажмите **Save**. После публикации GitHub покажет адрес сайта в этом же разделе.

## Загрузка на GitHub

Создайте репозиторий с именем `ci-cd-website`, затем выполните в терминале VS Code из папки проекта:

```bash
git init
git branch -M main
git add .
git commit -m "Создан сайт и настроен CI"
git remote add origin https://github.com/ВАШ_ЛОГИН/ci-cd-website.git
git push -u origin main
```

Если Git уже настроен в этой папке, не повторяйте `git init` и `git remote add origin`; проверьте адрес командой `git remote -v`.
