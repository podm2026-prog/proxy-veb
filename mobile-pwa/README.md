# ProxyPilot Mobile PWA

Мобильная адаптация расширения ProxyPilot в виде Progressive Web App (PWA).

## Структура

```
mobile-pwa/
├── index.html          — HTML-разметка, 3 экрана + нижняя навигация
├── app.css             — Стили: тёмная/светлая тема, glassmorphism, адаптив
├── app.js              — Логика: state в localStorage, сервисы, настройки
├── manifest.webmanifest — PWA манифест (иконки, название, тема)
└── sw.js               — Service Worker для офлайн-режима
```

## Экраны

| Экран | Функции |
|-------|---------|
| **Главная** | Включение прокси, список сервисов (preset grid), свои домены |
| **Настройки** | Тип прокси (ручной / свой пул / бесплатный), проверка |
| **О нас** | Информация о разработчике, инструкция по установке расширения |

## Запуск локально

```bash
# Нужен HTTPS или localhost для PWA-фич
npx serve e:/proxy-veb/mobile-pwa
# или
python -m http.server 3000 --directory mobile-pwa
```

Открой `http://localhost:3000` на телефоне (в одной WiFi-сети).

## Деплой на GitHub Pages

1. Создай репозиторий на GitHub
2. `git remote add origin <repo-url>`
3. `git push -u origin master`
4. Включи Pages в настройках репо (папка `mobile-pwa/`)

После деплоя Android покажет предложение «Добавить на главный экран».

## Установка в браузерах (расширение)

| Браузер | Инструкция |
|---------|-----------|
| **Chrome** (Desktop) | `chrome://extensions` → Режим разработчика → Загрузить распакованное → папка `proxypilot-chrome-0.12.0` |
| **Яндекс.Браузер** | `browser://extensions` → то же самое |
| **Firefox Android** | Поиск в Firefox Add-ons Store |
| **Kiwi Browser** (Android) | Меню → Расширения → Загрузить из файла |

## Технологии

- Vanilla HTML/CSS/JS — никаких зависимостей
- PWA: Service Worker + Web App Manifest
- localStorage для хранения настроек
- CSS Custom Properties для тём
- `safe-area-inset` для поддержки iPhone notch
