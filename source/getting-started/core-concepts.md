Прежде чем писать какой-либо код Ember, стоит ознакомиться с принципами работы приложений на базе этого фреймворка.

![ember core concepts](/static/images/guides/ember-core-concepts/ember-core-concepts.png)

## Роутер и обработчики маршрутов

Представьте, что вы пишите для сайта веб-приложение, которое дает пользователям возможность составить список собственности со стоимостью аренды. В любой момент вы должны суметь ответить на такие вопросы, как: Какую собственность просматривают пользователи? Редактируют ли они текущий элемент в списке? В Ember.js ответы на эти вопросы определяются адресом URL. URL можно установить несколькими способами:

* Пользователь загружает приложение в первый раз.
* Пользователь меняет URL вручную, например, щелкает по кнопке возврата или редактирует строку поиска.
* Пользователь щелкает по ссылке в приложении.
* Некоторые события в приложении приводят к изменению URL.

Независимо от того, как установлен URL, роутер Ember сопоставляет текущий URL с обработчиком маршрута. В таком случае обработчик маршрута выполняет следующее:

* Отображает шаблон.
* Загружает модель, доступную для шаблона.

## Шаблоны

В Ember.js шаблоны используются, чтобы произвести отображение HTML в приложении.

Большинство шаблонов в кодовой базе Ember довольно похожи и выглядят как обычный фрагмент HTML. Например:

```hbs
<div>Hi, this is a valid Ember template!</div>
```

Шаблоны Ember используют синтаксис шаблонов [Handlebars](http://handlebarsjs.com/). Все, что допустимо для синтаксиса Handlebars, допустимо и для синтаксиса Ember.

Шаблоны могут отображать свойства, которые предоставляются им из контекста, то есть либо компонентом, либо контроллером (формально, контроллер представляет шаблону модель из маршрута, но это редко используется в современных приложениях Ember и вскоре устареет). Например:

```hbs
<div>Hi {{name}}, this is a valid Ember template!</div>
```

Здесь `{{name}}` — это свойство, предоставленное контекстом шаблона.

Помимо свойств, двойные фигурные скобки (`{{}}`) могут содержать помощники и компоненты, которые мы обсудим позднее.

## Модели

Модели представляют собой устойчивое состояние.

Например, приложение для учета арендной платы должно сохранять детали стоимости, когда пользователь ее публикует. Поэтому арендная плата будет иметь модель, которая определяет эти детали. Скажем, модель будет называться *rental*.

Модель обычно сохраняет информацию на веб-сервере, хотя ее можно настроить так, чтобы сохранять данные где угодно, например, на локальном хранилище браузера.

## Компоненты

Шаблоны определяют, как будет выглядеть пользовательский интерфейс, а компоненты отвечают за то, как этот интерфейс будет себя *вести*.

Компоненты состоят из двух частей: шаблона, написанного в Handlebars, и исходного файла на JavaScript, который определяет поведение компонента. Например, приложение для учета арендной платы может иметь компонент `all-rentals` для отображения списка собственности с ценой аренды и `rental-tile` — для отдельной записи. Компонент `rental-tile` должен определять поведение, которое даст пользователю возможность скрывать и показывать изображение дома или квартиры.

Давайте рассмотрим эти ключевые концепции в деле и в следующих уроках создадим приложение для учета арендной платы.