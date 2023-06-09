## Техническое задание

Разработать одностраничное web-приложение. Весь  код поместитить в один файл index.html. Все внешние зависимости подключать из облачных CDN.

1. На странице должна быть отображена таблица (использовать таблицы Bootstrap). После загрузки страницы обратиться к API для получения списка приложений и заполнить ими таблицу.

2. В каждой строке таблицы сделать кнопку для изменения приложения. При нажатии на эту кнопку показать модальное окно (Bootstrap) и заполнить его данными конкретного приложения. Все данные в модальном окне, кроме app_id - доступны для редактирования, app_id - доступно только чтение.

3. Внизу модального окна 2 кнопки - "Закрыть" и "Сохранить". При нажатии на кнопку "Сохранить" - вызывается API для изменения приложения. В ответ приходит объект {"error":"0"} или {"error":"1"}. Если error=0 - закрываем модальное окно и обновляем список приложений в таблице (должны измениться данные приложения в таблице). Если error=1 вывести сообщение об ошибке. Ошибка возникает, если не найдено приложение с указанным app_id.

4. Над таблицей сделать кнопку "Добавить приложение". При нажатии на кнопку показать модальное окно (аналогичное по полям п. 2). Все поля пустные и доступны для редактирования. 

5. Внизу модального окна 2 кнопки - "Закрыть" и "Сохранить". При нажатии на кнопку "Сохранить" - вызывается API для создания приложения. В ответ приходит объект {"error":"0"} или {"error":"1"}. Если error=0 - закрываем модальное окно и обновляем список приложений в таблице (должно появиться новое приложение). Если error=1 вывести сообщение об ошибке. Ошибка возникает, приложение с указанным app_id уже существует. app_id не должен повторяться - протестировать это. Ошибка должна выводить прямо в модальном окне текстом.

6. Подключить библиотеку Chart.js. Разместить внизу страницы столбиковую диаграмму.

## Технологии

 - JQuery
 - Bootstrap 5
 - Chart.js

## Описание работы

1. Сразу после загрузки страницы делается fetch запрос к серверу и подтягиваются данные приложений. Данные переводятся в более удобный формат (объединяются из нескольких массивов в один). Далее проходимся по массиву данных и создаём в таблице соответствующие строки.

2. При нажатии на "изменить приложение" открывается модальное окно. Обработчик события определяет, какая кнопка была нажата (берёт из event.target), и из датасета этой кнопки получает id приложения, которое надо изменить. Дальше находит остальные данные приложения на основе id и заполняет ими поля формы открывшегося модального окна. Поле id недоступно для редактирования.

3. При нажатии "добавить приложение" открывается модальное окно, в котором можно указать данные для создания нового приложения. Если оно будет успешно создано, то автоматически добавится в таблицу.

4. При нажатии кнопки "сохранить" в обоих модальных окнах происходит валидация форма. Сначала делается проверка на то, что поля не пустые. Дальше корректность введённых данных должен подтвердить сервер (делается fetch запрос).

5. С помощью библиотеки Chart.js рисуется диаграма с указанными данными.

## Скриншоты

Основная страница:

![Скрин основной страницы](https://github.com/amfatw/test-apps-table/raw/main/screen1.jpg)

Модальное окно:

![Скрин модального окна](https://github.com/amfatw/test-apps-table/raw/main/screen2.jpg)