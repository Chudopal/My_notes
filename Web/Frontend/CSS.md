# CSS - Cascading Style Sheets.
позволяет отделить стильл от контента
+ [Основы SCC. Применение.](#sccforhtml)
+ [CSS в html](#cssinhtml)
+ [Шрифты](#fonts)
+ [Блочная модель CSS](#block)
+ [Расположеие](#position)

### <a name="sccforhtml"></a> Основы SCC. Применение.
CSS состоит из правил стилей, которые браузер интерпретирует, а затем применяет к соответствующим элементам в документе.
Правило стиля состоит из трех частей: **селектор, свойство и значение**.
Объявление CSS всегда заканчивается точкой с запятой, а группы объявлений заключаются в фигурные скобки.
Селектор указывает на элемент, к которому применять:
```CSS
    h1 { color: orange; }
```
    Код выше сделает все загловки с тегом `<h1>` оранжевыми.
+ **Селекторы типов**:
    Выбирают все объекты данного типа и применяют к ним стили. Чтобы выбрать по типу, перед селектором **не надо ничего ставить**:
    ```CSS
    p {
       color: red;
       font-size:130%;
    }
    ```
        Данный пример сделает весь текст в параграфах красным и увеличит шрифт в 130%.
+ **Селекторы классов**:
    Применяются к определенным классам. В классы могу быьб объеденины много элементов. Они как ID, которое можно применить сразу к нескольким объектам. Чтобы выбрать по классу, перед селектором **ставится точка**:

    HTML:
    ```HTML
    <div>
        <p class="first">This is a paragraph</p>
        <p> This is the second paragraph. </p>
    </div>
    <p class="first"> This is not in the intro section</p>
    <p> The second paragraph is not in the intro section. </p>
    ```
    CSS:
    ```CSS
    .first {font-size: 200%;}
    ```
+ **Селекторы по ID**:
    ID присваиваются одному элементу. Следовательно, если селектор по ID, то стили будут применены только к одному элементу на странице. Чтобы выбрать по ID, перед селектором **ставится хэш-символ**;

    HTML:
     ```HTML
    <div id="intro">
       <p> This paragraph is in the intro section.</p>
    </div>
    <p> This paragraph is not in the intro section.</p>
     ```
    CSS:
    ```CSS
    #intro {
       color: white;
       background-color: gray;
    }
    ```

Потомки селекторов - это селекторы, которые находятся внутри других селекторов. Можно обращатся к потомкам селекторов. Можно выбрать столько уровней, сколько надо

HTML:
```HTML
<div id="intro">
    <p class="first">This is a <em> paragraph.</em></p>
    <p> This is the second paragraph. </p>
</div>
<p class="first"> This is not in the intro section.</p>
<p> The second paragraph is not in the intro section. </p>
```
CSS:
```CSS
#intro .first em {
   color: pink; 
   background-color: gray;
}
```

### <a name="cssinhtml"></a> CSS в html
+ **Встроенный**:
    Определяетя внутри тега и только к нему и применяется. Чтобы использовать его, необходимо использовать атрибут `style=""` внутри нужного тега:
    ```html
    <p style="color:white; background-color:gray;">
        This is an example of inline styling. 
    </p>
    ```
+ **Внутренний**:
    Опеределяеются внутри элемента `<style>` внутри раздела `head` HTML-страницы:
    ```html
    <html>
       <head>
          <style>
          p {
             color:white;
             background-color:gray;
          }
          </style>
       </head>
       <body>
          <p>This is my first paragraph. </p>
          <p>This is my second paragraph. </p>
       </body>
    </html>
    ```   
+ **Внешний**:
    Отделяется от html в отдельный файл с расширением .css. Затем на этот CSS-файл ссылаются в HTML с помощью тега `<link>`. Элемент `<link>` находится внутри раздела head:

    HTML:
    ```html
    <head>
       <link rel="stylesheet" href="example.css">
    </head>
    <body>
       <p>This is my first paragraph.</p>
       <p>This is my second paragraph. </p>
       <p>This is my third paragraph. </p>
    </body>
    ```
    CSS:
    ```css
    p {
       color:white;
       background-color:gray;
    }
    ```
### <a name="fonts"></a> Шрифты
+ Свойство **`font-family`** *определяет шрифт* для элемента. Разделяя шрифты запятыми, можно   указать какой шрифт использовать в первую очередь, а какой (при отсуствии первого в системе)  испльзовать в качестве замены:

    HTML:
    ```html
    <p class="serif">
       This is a paragraph shown in serif font.
    </p>
    <p class="sansserif">
       This is a paragraph shown in sans-serif font.
    </p> 
    <p class="monospace">
       This is a paragraph shown in monospace font.
    </p> 
    <p class="cursive">
       This is a paragraph shown in cursive font.
    </p> 
    <p class="fantasy">
       This is a paragraph shown in fantasy font.
    </p> 
    ```
    CSS:
    ```css
    p.serif {
       font-family: "Times New Roman", Times, serif;
    }
    p.sansserif {
       font-family: Helvetica, Arial, sans-serif;
    }
    p.monospace {
       font-family: "Courier New", Courier, monospace;
    }
    p.cursive {
       font-family: Florence, cursive;
    }
    p.fantasy {
       font-family: Blippo, fantasy;
    }
    ```
+ Свойство **`font-size`** устанавливает *размер* шрифта:
    + xx-small - самый маленький
    + small - маленький
    + medium - средний
    + large - большой
    + larger - самый большой.
    Лучше использовать ключевые слова, так как каждый они адаптируются под каждый браузер или мобильное устройство:

    HTML:
    ```html
    <p class="small">
        Paragraph text set to be small
    </p>
    <p class="medium">
       Paragraph text set to be medium
    </p>
    <p class="large">
       Paragraph text set to be large
    </p>
    <p class="xlarge">
       Paragraph text set to be very large
    </p>
    ```
    CSS:
    ```css
    p.small {
        font-size: small;
    }
    p.medium {
       font-size: medium;
    }
    p.large {
       font-size: large;
    }
    p.xlarge {
       font-size: x-large;
    }
    ```
    Также можно в пискелах:
    ```css
    h1 { 
       font-size: 20 px ; 
    }
    ```
    Или в относительных единицах
    ```css
    h1 { 
       font-size: 1,25 em ; 
    }
    ```
+ Свойство **`font-style`** используется *для стиля текста*. Это свойство имеет 3 параметра:
    + normal - нормальный
    + italic - курсивный
    + oblique - наклонный

    ```css
    p.italic {
       font-style: italic;
    }
    ```
+ Свойство **`font-weight`** указывает вес шрифта:
    + normal - обычный
    + bold - жирный
    + bolder - жирнее
    + lighter - светлее
    ```css
    p.light {    
        font-weight:  lighter ; 
    } 
    p.bold {    
       font-weight:  bold ; 
    } 
    p.bolder { 
       font-weight:  bolder ; 
    }
    ```
    Так же можно указывать числом вес шрифта (от 100 до 900):
    ```css
    p.thicker {
       font-weight: 700;
    }
    ```
+ Свойство **'color'** - для цвета:
    ```css
    p.example {
       color: green;
    }
    h1 {
        color: #0000FF;
    }
    p.example {
       color: rgb(255,0,0);
    }
    ```
+ Свойство **`text-align`** - *выравнивает текст*:
    + left - по левому краю
    + right - по правому
    + center - по центру
    + justify - как в журнале, каждая строчка одинакового размера
    ```css
    p.left { 
    text-align: left ; 
    } 
    p.right { 
       text-align: right ; 
    } 
    p.center { 
       text-align: center ; 
    }
    ```
+ Свойство **`vertical-align`** - выравнивает текст *вертикально*:
    + top - вверху
    + middle - посередине
    + bottom - внизу

    HTML
    ```html
    <table border="1" cellpadding="2" cellspacing="0" style="height: 150px;">
      <tr>
         <td class="top">Top</td>
         <td class="middle">Middle</td>
         <td class="bottom">Bottom</td>
      </tr>
    </table>
    ```
    CSS:
    ```css
    td.top {
        vertical-align: top;
    }
    td.middle {
       vertical-align: middle;
    }
    td.bottom {
       vertical-align: bottom;
    }
    ```
+ Свойство **`text-decoration`** - как будет *декорирован* текст:
    + none - обычный текст
    + inherit - наследует это свойство от родительского элемета
    + overline - горизонтальная линия над текстом
    + underline - горизонтальная линия под текстом
    + line-through - зачеркивает текст
    ```css
    p.none {
        text-decoration: none;
    }
    p.inherit {
       text-decoration: inherit;
    }
    p.overline {
       text-decoration: overline;
    }
    p.underline {
       text-decoration: underline;
    }
    p.line-through {
       text-decoration: line-through;
    }
    ```
+ Свойство **`text-indent`** - показывает, сколько *расстояния нужно отсавить до начала первой строки*:
```css
p { 
   text-indent : 60px; 
}
```
+ Свойство **`text-shadow`** - добавляет *тень* тексту.Он принимает четыре значения: первое значение определяет расстояние тени в направлении **x** (по горизонтали) , второе значение задает расстояние в направлении **y** (по вертикали) , третье значение определяет **размытие** тени и четвертое значение устанавливает **цвет**:
```css
h1 {
   color: blue;
   font-size: 30pt;
   text-shadow: 5px 2px 4px grey;
}
```
+ Свойство **`text-transform`** *трансформирует текст*:
    + capitalize - каждое слово с большой буквы
    + uppercase - все буквы в верхнем регистре
    + lowercase - все буквы в нижнем регистре
    ```css
    p.uppercase {
        text-transform: uppercase;
    }
    p.lowercase {
       text-transform: lowercase;
    }
    ``` 
+ Свойство **`letter-spacing`** - определяет *расстояние между буквами* в тексте:
    + normal - по умолчанию
    + length - определяет дополнительный пробел между символами, с использованием таких единиц измерения, как px, pt, cm, mm и т. д..
    + inherit - наследует свойство от его родительского элемента;
    ```css
    p.positive { 
        letter-spacing: 4px; 
    }
    p.negative { 
       letter-spacing: -1.5px; 
    } 
    ```
+ Свойство **`word-spacing`** - *расстояние между словами*:
```css
p.normal { 
   word-spacing: normal;
}
p.px { 
   word-spacing: 30px;
}
```

### <a name="block"></a> Блочная модель CSS
+ Все элементы HTML могут рассматриваться как блоки. Блочная модель CSS представляет дизайн и верстку сайта. Она состоит из  **margins(полей), borders(границ), paddings(отступов), content(содержимого)**. Свойства работают таком порядке: **top -> right -> bottom -> left**.
![](./PICTURES/block_model.png)
+ **Общая высота элемента = высота + верхний отступ + нижний отступ + верхний край + нижний край + верхний край + нижний край**
+ Свойство **`border`** позволяет настраивать графницы элементов. Чтобы добавить границу к элементу, нужно указать **размер, стиль и цвет рамки**:
    ```css
    p {
       padding: 10px;    
       border: 5px solid green;
    }
    ```
+ Свойство **`border-width`** - указывает толщину обводки около элемента:
    ```css
    p.first {
       padding: 10px;    
       border-style: solid;
       border-width: 2px;
    }
    p.second {
       padding: 10px;    
       border-style: solid;
       border-width: 5px;
    }
    ```
    ```css
    p.first {
        padding: 10px;
        border-style: solid;
        border-width: 2px;
        border-color: blue;
    }
    p.second {
       padding: 10px;    
       border-style: solid;
       border-width: 2px;
       border-color: #FF6600;
    } 
    p.third {
       padding: 10px;    
       border-style: solid;
       border-width: 2px;
       border-color: rgb(0, 153, 0);
    } 
    ```
+ Свойство **`border-style`** для настройки обводки:
    ```css
    p.none {border-style: none;}
    p.dotted {border-style: dotted;}
    p.dashed {border-style: dashed;}
    p.double {border-style: double;}
    p.groove {border-style: groove;}
    p.ridge {border-style: ridge;}
    p.inset {border-style: inset;}
    p.outset {border-style: outset;}
    p.hidden {border-style: hidden;}
    ```
    ![](./PICTURES/border.png)

+ Свойства **`width`** и **`height`** определяют ширину и высоту бокса без учета границ. Можно задавать пикселами и процентами
    ```css
    div {
       border: 5px solid green;    
       width: 90px````;
       height: 90px;
    }
    ```
    Данный элемент будет 100х100.
    + min-width - минимальная ширина элемента
    + min-height - минимальная высота элемента
    + max-width - максимальная ширина элемента
    + max-height - максимальная высота элемента.
    ```css
    p.first {
       border: 5px solid green;    
       min-height: 100px;       
    }
    p.second {
       border: 5px solid green;    
       max-width: 100px;       
    }
    ```
+ Свойство **`background-color`** позволяет изменять цвет фона заданного тега:
    ```css
    body {
        background-color: #87CEFA;
    }
    ```
+ Свойство **`background-image`** позволяет задать *картинку фона*:
    ```css
    body {
       background-image: url("css_logo.png");
       background-color: #e9e9e9;
    }
    ```
    *URL указывает путь к файлу изображения. Поддерживаются как относительные, так и абсолютные пути.*
+ Свойство **`background-repeat`** задает *повторение* какой-либо картинки на фоне. Она может повторятся вертикально, горизонтально или вообще не повторяться:
    ```css
    body {
       background-image: url("css_logo.png");
       background-repeat: repeat-x;  
    }
    ```
    ```css
    body {
       background-image: url("css_logo.png");
       background-repeat: repeat-y;
    }
    ```
+ Свойство **`background-attachment`** устанавливает, является ли фоновое изображение фиксированным или прокручивается с остальной частью страницы:
    + fixed - фиксированное
    + scroll - прокручивается
    ```css
    body {
       background-image: url("css_logo.png");
       background-repeat: no-repeat;
       background-attachment: scroll;
    }
    ```
+ Установка стилей для **ссылок**:
    Для ссылок можно использовать любое свойство CSS (например, color, font-family, background и т. Д.). кроме того существуют определенные псоевдоселекторы, которые помогают контролировать ссылки:
    + a:link - непосещенная ссылка
    + a:visited - посещенная ссылка
    + a:active - ссылка станвится активной, если щелкнуть на нее
    + a:hover - при наведении на ссылку.
    HTML:
    ```html
    <p><a href="http://www.sololearn.com" target="_blank">
       This link is hovered when we mouse over it
    </a></p>
    ```
    CSS:
    ```css
    a:hover {
       color: red;
    }
    ```
+ Свойство **`cursor`** может изменять курсор:
![](./PICTURES/cursor.png)

### <a name="position"></a> Расположение
+ Свойство **`display`** выстраивает элементы определенным образом:
    + `block` - каждый элемент будет являеться блоком. Блочный элемент - это элемент, который занимает всю доступную ширину с разрывами строки до и после.
    + `inline` - все элементы выстраиваются в одну строку.
    + `none` - элементы вообще не отображаются.
    ```css
    span { 
       display: block; 
    }
    ```
+ Свойство **`visibility`** указывает виден ли элемент:
    + `visible` - виден.
    + `hidden` - скрыт.
+ Свойство **`position`** - предназанчено для позиционирования элементов, относительно параметров `top`, `right`, `bottom`, `left`:
    + **static** - статический элемент позиционируется относительно обычного вида страницы:
        ```css
        p.position_static {
           position:static;
           top: 30px;
           right: 5px;
           color: red;
        }
        ```
    + **fixed** - позиционирование относительно окна браузера:
        ```css
        p.position_fixed {
           position: fixed;
           top: 30px;
           right: 5px;
           color: red;
        }
        ```
    + **relative** - позиционирование относительно обычного положения элемента:
        ```css
        span {
           background: green;
           color:white;
           position: relative;
           top: 150px;
           left: 50px;
        }
        ```
+ Свойство **float** позволяет вставлять элемент так, чтобы другие элементы могли обтекать его. Распологать элемент можно при помощи ключевых слов **left , right и none**:
    ```css
    img { 
       float: right ; 
    }
    ```
+ Свойство **`overflow`** - определяет поведение элемента, когда он переполнен:
    + **scroll** - добавляет скроллбар чтобы остальная часть контента была видна:
        ```css
        div {
           width: 150px;
           height: 150px;
           background-color: LightBlue;
           float: left;
           overflow: scroll;
        }
        ```
    + **auto** - если переполняется, то автоматически добавляется скроллбар.
    + **hidden** - если переполняется, то переполненная часть контента не видна:
        ```css
        div {
           width: 150px;
           height: 150px;
           background-color: LightBlue;
           float: left;
           overflow: hidden;
        }
        ```
+ Свойство **`z-index`** определяет, какой элемент будет над каким, если один элемент заходит на часть другого. Чем ниже его значение, тем ниже в стеке он будет находиться:
    ```css
    .blue {
       z-index: 3; 
       position: relative;
    }
    .red {
       z-index: 2;
       position: relative;
    }
    ```
    ![](./PICTURES/rect.png)