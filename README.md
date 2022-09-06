# HtmlMakeup

### Блочная верстка
Существуют различные способы верстки. 
Раньше распространенным способом верствки была верстка на основе таблиц. 
Таблицы позволяет разделить вcе пространство веб-страницы на строки и столбцы.
Минус табличной верстки в том, что она не гибкая.
На замену пришла блочная верстка.
Блочная верстка - это когда для разметки используется CSS-свойство float, а основным элементов является элемент div.
В начале определим все блоки. 
```
<section id="header">header</section>
<div id="main">main</div>
<section id="footer">footer</section>
<style>
  #header {
    background-color: #ccc;
    height: 200px;
  }
  #main {
    background-color: #ddd;
    height: 1000px;
  }
  #footer {
    background-color: #eee;
    height: 200px;
  }
  body{
      margin:0;
      padding:0;
  }
</style>


```  
 ### Эффект обтекания
 - Чтобы переместить блок сайдбара вправо по отношению к блоку основного содержимого , нам надо указать свойство float: right и ширину.

```
<style>
  #header {
    background-color: #ccc;
    height: 200px;
    float:right;
    width:200px;
  }
  #main {
    background-color: #ddd;
    height: 1000px;
    margin-right: 200px;
  }
  #footer {
    background-color: #eee;
    height: 200px;
    margin-right: 200px;
  }
  body{
      margin:0;
      padding:0;
  }
</style>

```
  
 
### Вложенные (плавающие) блоки
- блок основного содержимого может включать блок собственно содержимого и блок меню
```
...
<div id="main">
  div main
  <section id="one">section one</section>
  <section id="two">section two</section>
  <section id="three">section three</section>
  <section id="four">section four</section>
</div>
...
```
```
...
#one,
  #two,
  #three,
  #four {
    background-color: #f7f7f7;
    margin: 10px;
    height: 200px;
  }

...
```
   
### Выравнивание столбцов по высоте
При блочной верстке можно столкнуться с проблемой высоты с столбцов, если плавающие блоки имеют определенный фон
-  решением проблемы является оборачивание в отдельный элемент, у которого устанавливается фон
```
...
<div id="wrapper">
  <section id="header">section header</section>
  <div id="main">
    div main
    <section id="one">section one</section>
    <section id="two">section two</section>
    <section id="three">section three</section>
    <section id="four">section four</section>
  </div>
  <section id="footer">section footer</section>
</div>
...
```
```
...
#wrapper {
    background-color: #ccc;
  }
  #header {
    height: 200px;
    float: right;
    width: 200px;
  }
...

```
### Свойство display
Кроме свойства float, которое позволяет изменять позицию элемента, есть еще одно важное свойство - display. Оно позволяет управлять блоком элемента и также влиять на его позиционирование относительно соседних элементов.
Это свойство может принимать следующие значения:
 - inline: элемент становится строчным, подобно словам в строке текста
- block: элемент становится блочным, как параграф
- inline-block: элемент располагается как строка текста
- list-item: элемент позиционируется как элемент списка обычно с добавление маркера виде точки или порядкового номера
- run-in: тип блока элемента зависит от окружающих элементов
- flex: позволяет осуществлять гибкое позиционирование элментов
- table, inline-table: позволяет расположить элементы в виде таблицы
- none: элемент не виден и удален из разметки html
```
<section id="header">
    <header>
        section header
    </header>
    <nav id="nav">
        <ul>
            <li>
                <a href="#one">One</a>
            </li>
            <li>
                <a href="#two">Two</a>
            </li>
            <li>    
                <a href="#three">Three</a>
            </li>
            <li><a href="#four">Four</a></li>
        </ul>
    </nav>
    <footer>
        social media icons
    </footer>
</section>
<div id="wrapper">
  <div id="main">
    div main
    <section id="one">section one</section>
    <section id="two">section two</section>
    <section id="three">section three</section>
    <section id="four">section four</section>
  </div>
  <section id="footer">section footer</section>
</div>
<style>
  /* ------------- основные блоки ---*/
  #wrapper {
    background-color: #ccc;
    padding-right: 200px;
  }
  #header {
    background: #4acaa8;
    color: #d2f2e9;
    height: 100%;
    /* float: right; */
    width: 200px;
    position: fixed;
    right: 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    text-align: center;
  }
  #header>nav ul{
      list-style: none;
      padding: 0;
  }
  #header>nav ul li{
    border-top: solid 2px #5ccfb1;
  }
  
  #main {
    background-color: #ddd;
    height: 1000px;
    /* margin-right: 200px; */
  }
  #footer {
    background-color: #eee;
    height: 200px;
    /* margin-right: 200px; */
  }

  /*------------------ вложенные блоки--*/
  #one,
  #two,
  #three,
  #four {
    background-color: #f7f7f7;
    margin: 10px;
    height: 200px;
  }
  /*-----------------------------------*/
  body {
    margin: 0;
    padding: 0;
  }
</style>


```
 
### Тестирование адаптивного дизайна
   - Google Chrome надо перейти в меню Дополнительные инструменты -> Инструменты разработчика
 
### Media Query
 - правила Media Query позволяют определить стиль в зависимости от размеров браузера
Например, чтобы применить стиль к мобильным устройствам мы можем написать так:
```


@media (min-width: 481px) and (max-width: 768px) {
  #wrapper {
    padding-right: 0px;
  }
  #header {
    width: 0px;
  }
}

@media (min-width: 769px) and (max-width: 1024px) {
  #wrapper {
    padding-right: 20em;
  }
  #header {
    width: 20em;
  }
}

@media (min-width: 1025px) and (max-width: 1280px) {
  #wrapper {
    padding-right: 21em;
  }
  #header {
    width: 21em;
  }
}

@media (min-width: 1281px) and (max-width: 1680px) {
  #wrapper {
    padding-right: 22em;
  }
  #header {
    width: 22em;
  }
}

```
