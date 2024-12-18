# Информационная система "Электронные визитки"

Информационная система "Электронные визитки" позволяет создавать, изменять просматривать электронные визитки, просматривать аналитику по ним

## 1. Структура функциональных возможностей (Mind Map)

```mermaid
mindmap
  root((ИC Электронные визитки))
    Пользователи
      Клиенты
        Регистрация
        Авторизация
        Работа с визитками
        Просмотр аналитики
      Модераторы
        Проверка визиток
    Работа с визитками
      Просмотр визиток
      Создание визиток
      Изменение визиток
      Модерация визиток
      Удаление визиток
      Генерация лендинга
    Аналитика по визиткам
      Обработка данных
      Генерация аналитики
    Авторизация и аутентификация
      Создание аккаунта
      Вход в аккаунт
    Архитектура
      Клиент-серверная
      Микросервисы
    Используемые технологии
      Spring
      Java
      React Native
      HTML, CSS, JS
      PostgeSQL
      Redis
    Задачи проектирования
      Дизайн системы
      Моделирование данных
      Проектирование API
      Оценка производительности

```

## 2. Диаграмма путешествия пользователя (User Journey Diagram)
Крит путь пользователя. Ииллюстрирует ключевые шаги клиента в процессе использования системы: от входа до завершения заказа.

```mermaid
journey
  title Общий путь пользователя при взаимодействии с ИС
  section Вход в аккаунт
    Пользователь открывает приложение: 5: Пользователь
    Пользователь выполняет авторизацию: 4: Пользователь
  section Создание визитки
    Пользователь вводит данные: 5: Пользователь
    Клиент отправляет запрос на сервер: 5: Клиент
    Сервер сохраняет визитку и генерирует лендинг: 4: Сервер
    Клиент показывает визитку и QR для неё: 4: Клиент
    Пользователь переходит на созданный лендинг: 4: Пользователь
  section Просмотр аналитики
    Пользователь заходит в раздел аналитики: 5: Пользователь
    Клиент отправляет запрос на сервер: 5: Клиент
    Сервер генерирует данные по аналитике: 4: Сервер
    Клиент рисует графики и отображает раздел: 5: Клиент
    Пользователь ознакамливается с аналитикой по визитке: 7: Пользователь
```

## 3. Квадрант-граф (Quadrant Chart)
```mermaid
quadrantChart
    title Приоритеты задач
    x-axis "Низкая срочность" --> "Высокая срочность"
    y-axis "Низкая важность" --> "Высокая важность"
    quadrant-1 "Срочные и важные"
    quadrant-2 "Важные, но не срочные"
    quadrant-3 "Не срочные и не важные"
    quadrant-4 "Срочные, но не важные"
    "Завершение разработки API сервисов": [0.8, 0.9]
    "Дизайн пользовательского интерфейса": [0.55, 0.8]
    "Исправление бага создания аналитики": [0.7, 0.4]
    "Оптимизация запросов к базе данных": [0.2, 0.3]
    "Оптимизация алгоритмов генерации аналитики": [0.2, 0.55]
    "Добавление возможности кастомизации внешнего вида лендингов": [0.3, 0.88]
```

## 4. Git-граф
Отображает историю разработки, включая основные ветки и слияния.

```mermaid
gitGraph
  commit id: "Initial commit"
  branch feature/CARDS-1-auth
  commit id: "CARDS-1 Implement user auth"
  commit id: "CARDS-1 Add tests"
  checkout main
  merge feature/CARDS-1-auth
  branch feature/CARDS-2-cards-actions
  commit id: "CARDS-2 Add crud"
  commit id: "CARDS-2 Add landing creation"
  commit id: "CARDS-2 Add moderation action"
  commit id: "CARDS-2 Add tests"
  checkout main
  merge feature/CARDS-2-cards-actions
  branch feature/CARDS-3-analytics
  commit id: "CARDS-3 implement saving data from landing"
  commit id: "CARDS-3 implement analytics for 1 day"
  commit id: "CARDS-3 implement analytics for 7 days"
  commit id: "CARDS-3 implement analytics for 30 days"
  commit id: "CARDS-3 implement data analysis"
  commit id: "CARDS-3 add tests"
  checkout main
  merge feature/CARDS-3-analytics
```