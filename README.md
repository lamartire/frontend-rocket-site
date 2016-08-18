![Catstruct](http://darkened.space/catstruct.jpg)

# Catstruct

## Таски и команды

Установка зависимостей:
```
npm i
```
Запуск сборки проекта с **отслеживанием изменений**:
```
npm start
```
Сборка проекта
```
npm build
```
Создание страницы с определнным шаблоном (по-умолчанию default):
```
npm run page pagename layoutname
```
Создание блока (создает папку с заданным именем и файлами pug/styl):
```
npm run block blockname
```
Упаковка папки `dist` в архив:
```
npm run zip
```
## Структура

```
├──app/
|	├──assets/ - ресурсы, которые используются в дальнейшем (пути сохраняются)
|	|   ├──fonts/ - шрифты
|	|   ├──images/ - картинки
|	|   ├──styles/ - скомпилированные стили и различные хелперы
|	|   |   ├──fonts.styl - подключение шрифтов (важно помнить, что путь до шрифтов остается таким же, как и в примере)
|	|   |   ├──main.styl - основной файл для компиляции, может иметь постфикс вида @ie9
|	|   |   ├──mixins.styl - примеси stylus'a
|	|   |   ├──variables.styl - переменные stylus'a
|	|   |   └──sprite.styl - генерируемый файл спрайтов
|	|   ├──sprites/ - папка для спрайтов (исходники для склейки)
|	|   ├──js/ - папка для скомпилированного js
|	|   └──coffee/ - папка для скомпилированного coffee
|	|
|	├──layouts/ - шаблоны pug
|	├──blocks/ - папки с блоками (pug + styl + js)
|	|
|	├──data/ - коллекция json-файлов с данными
|	|
|	├──helpers/ - различные хелперы
|   |   └──pug/
|	|       ├──import.pug - все импорты pug зависимостей (генерируется автоматически)
|   |       └──bemto/ - БЭМ для pug
|	|
|	├──main.js - js-файл, для подключения зависимостей
|	|
|	└──pages/ - файлы с разметкой страниц
|
├──core/
|   ├─tasks/
|   ├─blocks-layouts/ - шаблоны для генерации блоков (сам скрипт в процессе разработки)
|   |
|   ├─create-block.js - скрипт герерации блока
|   ├─create-block-from-layout.js - скрипт герерации блока по шаблону
|   ├─fonts.js - скрипт импорта шрифтов
|   └─create-page.js - скрипт герерации страницы
|
└──.browsers - список браузеров, которым будет собираться "персональный" файл стилей
```

## Поддержка `ie9` и прочих версий

Чтобы реализовать "рукописную" поддержку CSS в IE, в особенности старых браузерах, в шаболне реализовано решение:

Создаем файл `blockname@ie9.styl`, на выходе получаем `main@ie9.css`, который можно спокойно подключать через псевдо-комментарии.

Чтобы шаблон знал, какие браузеры войдут в сборку, нужно указать их список в корне лежит файл `.browsers`.

Указываем в нем список версий ie:

```
ie9 ie8
```

Создаем файлы стилей описанные выше, на выходе получим "персональные" файлы стилей, для этих браузеров.

## Быстрый импорт шрифтов

Для того, чтобы быстро создать файл с переменными для шрифтов, нужно указать имена нужных шрифтов в файле `.fonts` разделенные пробелами, далее положить файлы шрифтов в папку `app/assets/fonts`, переименовать файлы согласно таблице:

| **Имя файла** | **Жирность щрифта** |
|---------------|---------------------|
| hairline      | 100                 |
| ultralight    | 200                 |
| light         | 300                 |
| regular       | 400                 |
| medium        | 500                 |
| semibold      | 600                 |
| bold          | 700                 |
| ultrabold     | 800                 |
| black         | 900                 |

Если файл будет содержать одно из этих сочетаний, будет создана соответствующая переменная. Например: для `OpenSansRegularItalic.ttf` будет сгенерирована переменная и код вида:

```
opensans = OpenSans

@font-face
	font-family OpenSans
		src: url('../fonts/OpenSansRegularItalic.ttf') format('ttf')

	font-weight 400
	font-style italic
```


### О шаблоне

Создание данного шаблона стало результатом вдохновения от [CSSSR Project template](https://github.com/CSSSR/csssr-project-template). Ребята, вы могете :)

Создавался около года и постепенно обрастал фичами. На данный момент, мне кажется он более-менее скомпанованным и способным приносить пользу.

А вообще, теперь и у меня есть свой велосипед!  :cat: