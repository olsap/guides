Ember CLI — интерфейс Ember с командной строкой. Он предоставляет структуру стандартного проекта, набор инструментов разработки и систему дополнений. Это позволяет разработчикам Ember сфокусироваться на создании приложения, вместо того чтобы отвлекаться на вспомогательные структуры, которые позволяют эти программы запускать. Чтобы получить список команд Ember CLI, в командной строке нужно набрать `ember --help`. Более подробную информацию по конкретной команде можно получить, если набрать `ember help <имя_команды>`.

## Создание нового приложения

Чтобы создать новый проект с помощью Ember CLI, используйте команду `new`. Для подготовки к обучению в следующем разделе, вы можете создать приложение под названием `super-rentals`.

```shell
ember new super-rentals
```

## Структура каталогов

Команда `new` генерирует структуру проекта со следующими файлами и директориями:

```shell
|--app
|--bower_components
|--config
|--dist
|--node_modules
|--public
|--tests
|--tmp
|--vendor

bower.json
ember-cli-build.js
package.json
README.md
testem.json
```

Давайте взглянем на сгенерированные Ember CLI папки и файлы.

**app**: Здесь хранятся папки и файлы для моделей, компонентов, маршрутов, шаблонов и стилей. Основная часть кода вашего проекта Ember находится здесь.

**bower_components/bower.json**: Bower — инструмент управления зависимостями. Он используется в Ember CLI, чтобы управлять плагинами front-end и зависимостями компонентов (HTML, CSS, JavaScript и т. д.). Все компоненты Bower устанавливаются в директорию `bower_components`. Если мы откроем `bower.json`, то увидим список зависимостей, которые устанавливаются автоматически, включая Ember, jQuery, Ember Data и QUnit (для тестирования). Если мы добавим зависимости front-end вроде Bootstrap, то увидим их в этом списке и директории `bower_components`.

**config**: Директория config содержит `environment.js`, где вы можете устанавливать конфигурации для приложения.

**dist**: Когда мы создаем приложение для развертывания, выходные файлы будут сформированы здесь.

**node_modules / package.json**: Эта директория и файл из npm. npm — менеджер пакетов для Node.js. Ember компонуется с Node.js и использует разнообразие его модулей для работы. Файл `package.json` содержит список текущих зависимостей npm для приложения. Любое дополнение Ember CLI, которое вы устанавливаете, также будет отображаться здесь. Пакеты, указанные в `package.json`, устанавливаются в директории node_modules.

**public**: Эта директория содержит ресурсы вроде изображений и шрифтов.

**vendor**: В этой директории находятся зависимости front-end (например, JavaScript или CSS), которые изначально не управляются Bower.

**tests / testem.json**: В папке `tests` находятся автоматизированные тесты для приложения, а исполнитель тестов Ember CLI testem настраивается в файле `testem.json`.

**tmp**: Здесь находятся временные файлы Ember CLI.

**ember-cli-build.js**: Этот файл описывает, как Ember CLI должен создавать приложение.

## Модули ES6

Если вы взгляните на `app/router.js`, то увидите синтаксис, который может быть вам незнаком.

`app/router.js`
```js
import Ember from 'ember';
import config from './config/environment';

var Router = Ember.Router.extend({
  location: config.locationType
});

Router.map(function() {
});

export default Router;
```

Ember CLI использует модули ECMAScript 6 (или просто ES6), чтобы организовать код приложения. Например, строка `import Ember from 'ember';` дает доступ к текущей библиотеке Ember.js как переменной `Ember`. А строка `import config from './config/environment';` дает доступ к данным конфигурации приложения как переменной `config`. В конце файла `export default Router;` делает переменную `Router`, определенную в этом файле, доступной для других частей приложения.

## Обновление Ember

Прежде чем углубляться в обучение, убедитесь, что у вас стоит самая последняя версия Ember. Если версии `ember` и `ember-data` в `bower.json` ниже версии, указанной в верхнем левом углу этого руководства, то обновите номер версии в `bower.json` и запустите `bower install`.

## Сервер разработки

Когда вы создаете новый проект, для проверки его работоспособности можно запустить сервер разработки Ember:

```shell
ember server
```

или более кратко:

```shell
ember s
```

Если вы перейдете по адресу `localhost:4200`, то увидите новое приложение с текстом "Welcome to Ember.js" (Добро пожаловать в Ember.js).