# gulp.webpack

## Особенности
* используются препроцессоры [Pug](https://pugjs.org/) и [SCSS](https://sass-lang.com/)
* используется транспайлер [Babel](https://babeljs.io/) для поддержки современного JavaScript (ES6) в браузерах
* используется [Webpack](https://webpack.js.org/) для сборки JavaScript-модулей

## Установка
* установите [NodeJS](https://nodejs.org/en/) (если требуется) и [Yarn](https://yarnpkg.com/en/docs/install)
* скачайте сборку в консоли с помощью [Git](https://git-scm.com/downloads): ```git clone https://github.com/romuelson/gulp.webpack.git```
* установите ```gulp``` глобально: ```yarn global add gulp-cli```
* перейдите в скачанную папку со сборкой: ```cd gulp.webpack```
* скачайте необходимые зависимости: ```yarn```
* чтобы начать работу, введите команду: ```yarn run dev``` (режим разработки)
* чтобы собрать проект, введите команду ```yarn run build``` (режим сборки)

Если вы всё сделали правильно, у вас должен открыться браузер с локальным сервером.
Режим сборки предполагает оптимизацию проекта: сжатие изображений, минифицирование CSS и JS-файлов для загрузки на сервер.

## Файловая структура

```
gulp.webpack
├── build
├── gulp_tasks
├── source
│   ├── assets
│   │   ├── fonts
│   │   ├── images
│   │   ├── scripts
│   │   └── styles
│   ├── views
│   │   ├── common
│   │   ├── layouts
│   │   └── pages
│   └── .htaccess
├── gulpfile.babel.js
├── webpack.config.js
├── package.json
├── .babelrc.js
├── .bemrc.js
├── .stylelintrc.json
├── .stylelintignore
└── .gitignore
```

* Корень папки:
    * ```.babelrc.js``` — настройки Babel
    * ```.gitignore``` – запрет на отслеживание файлов Git'ом
    * ```.stylelintrc.json``` — настройки Stylelint
    * ```.stylelintignore``` – запрет на отслеживание файлов Stylelint'ом
    * ```gulpfile.babel.js``` — настройки Gulp
    * ```webpack.config.js``` — настройки Webpack
    * ```package.json``` — список зависимостей
* Папка ```source``` - используется во время разработки:
    * шрифты: ```source/assets/fonts```
    * изображения: ```source/assets/images```
    * JS-файлы: ```source/assets/scripts```
    * SCSS-файлы: ```source/assets/styles```
    * страницы сайта: ```source/views/pages```
    * служебные Pug-файлы: ```source/views```
    * конфигурационный файл веб-сервера Apache с настройками [gzip](https://habr.com/ru/post/221849/) (сжатие без потерь): ```source/.htaccess```
* Папка ```build``` - папка, из которой запускается локальный сервер для разработки (при запуске ```yarn run dev```)
* Папка ```gulp_tasks``` - папка с Gulp-тасками

## Команды
* ```yarn run lint:styles``` - проверить SCSS-файлы. Для VSCode необходимо установить [плагин](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint). Для WebStorm
или PHPStorm необходимо включить Stylelint в ```Languages & Frameworks - Style Sheets - Stylelint``` (ошибки будут исправлены автоматически при сохранении файла)
* ```yarn run lint:styles --fix``` - исправить ошибки в SCSS-файлах
* ```yarn run dev``` - запуск сервера для разработки проекта
* ```yarn run build``` - собрать проект с оптимизацией без запуска сервера
* ```yarn run build:views``` - скомпилировать Pug-файлы
* ```yarn run build:styles``` - скомпилировать SCSS-файлы
* ```yarn run build:scripts``` - собрать JS-файлы
* ```yarn run build:images``` - собрать изображения
* ```yarn run build:webp``` - сконвертировать изображения в формат ```.webp```
* ```yarn run build:sprites```- собрать спрайты
* ```yarn run build:fonts``` - собрать шрифты
* ```yarn run build:favicons``` - собрать фавиконки
* ```yarn run build:gzip``` - собрать конфигурацию Apache

## Рекомендации по использованию

### Сторонние библиотеки
* все сторонние библиотеки устанавливаются в папку ```node_modules```
    * для их загрузки воспользуйтеcь командой ```yarn add package_name```
    * для подключения JS-файлов библиотек импортируйте их в самом начале JS-файла БЭМ-блока (то есть тот БЭМ-блок, который использует скрипт), например:
    ```javascript
    import $ from 'jquery';
    ```