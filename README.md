



С title/description нашел пока такой выход:
Если самая первая строка в README.md "простой текст", а не заголовок, то title/description берутся из _config.yml



#  HTML-and-CSS 
## Qgis Processing plugin

<!-- TOC -->

- [HTML-and-CSS](#html-and-css)
	- [Qgis Processing plugin](#qgis-processing-plugin)
		- [1. - Finestra processing](#1---finestra-processing)
		- [2. - OPZIONI](#2---opzioni)
		- [3. CSS - ESEMPIO ARIAL FIXED](#3-css---esempio-arial-fixed)
- [4. Dati di esempio](#4-dati-di-esempio)
- [5. Videotutorial](#5-videotutorial)
- [6. Ringraziamenti](#6-ringraziamenti)

<!-- /TOC -->

### 1. - Finestra processing
Il plugin, una volta caricato, compare negli script di processing nella cartella HTML

Il plugin permette la composizione di una pagina HTML con i dati da una fonte tra quelle compatibili.



1. sorgente dati, eventualmente anche filtrati e/o solo selezionati se da mappa;
2. selettore campi dati da inserire nell'html;
3. [opzionale] espressione filtro;
4. [opzionale] titolo in testa alla pagina html;
5. [opzionale] icona o immagine in alto a sinistra;
6. [opzionale] css da includere nell'html;
7. dimensioni icona e foto;
8. scelta tra link con percorso assoluto (default) o relativo;
9. file in uscita.

Il plugin riconosce i campi data e quelli in cui è memorizzata l'immagine o le immagini purchè con estensione di file immagine (gif; jpeg; jpg; png; svg).

I campi selezionati possono essere riordinati a piacimento.

Le dimensioni dell'icona e delle immagini possono essere espresse in tutte le unità di misura previste dall'html.

Il file css determina tutte le caratteristiche estetiche del file prodotto, riferendosi sempre all'elemento 'Table', alt tag **'b'** per il titolo ed al tag **'div'** per l'immagine o l'icona in intestazione.

I file prodotti, se temporanei, avranno sempre percorsi assoluti, altrimenti non sarebbero funzionanti, se salvati possono avere sia percorsi assoluti sia relativi.

Per poter eventualmente traferire il progetto con i file html relativi, tutti i file devono risiedere in sottocartelle della cartella di progetto.

Lo script effettua una serie di controlli sulla congruenza dei percorsi dei file origine (sorgente, css, icona/immagine) e avverte se
c'è la possibilità che il file html prodotto possa non funzionare correttamente.

Per default il percorso di progetto viene considerato per primo, in seconda scelta il percorso del file sorgente.

_NOTA BENE: 
Con i file temporanei, se i campi contengono percorsi relativi, l'html prodotto non avrà le immagini correttamente visualizzate._

↑[torna su](#HTML-and-CSS )↑

### 2. - OPZIONI

1. Espressione filtro: un filtro componibile nativo di QGIS;
2. Titolo: una qualsiasi combinazione alfanumerica nella casella di testo, senza apici, il sistema la mette in rosso, ma funziona perfettamente; altrimenti una qualsiasi composizione entro il solito calcolatore, ovviamente si tratta di una scritta non dinamica;
3. Icona o immagine: una qualsiasi immagine tra quelle compatibili:
4. CSS: questa è la parte più interessante dato che permette una personalizzazione accurata della pagina html prodotta. Come anzidetto i tag utilizzati sono **'Table'**, **'b'** e **'div'**, per generare comodamente il css vi sono diversi tools gratuiti online tra cui **https://divtable.com/table-styler/** che permette con pochi passaggi di ottenere risultati veramente notevoli e la cui unica limitazione è la fantasia dell'autore. Il sito da anche la possibilità di definire ogni singolo aspetto dell'impaginazione.

↑[torna su](#HTML-and-CSS )↑

### 3. CSS - ESEMPIO ARIAL FIXED
A titolo di esempio ecco un css:
```
`/* Personalizzazione Titolo */
b {
	font-family: Arial;
	font-size: 24pt;
	letter-spacing: 0.1px;
	word-spacing: 0.2px;
	color: #000000;
}
/* Caratteristiche generali della tabella */
table.Table {
	font-family: Arial;
	font-size: 12pt;
	letter-spacing: 0.1px;
	word-spacing: 0.2px;
	color: #000000;
	font-weight: normal;
	text-decoration: none;
	font-style: normal;
	font-variant: normal;
	text-transform: none;
	border: 1.5px solid #674d3c;
	background-color: #fff2df;
	border-collapse: collapse;
	width: 145mm;
}
/* Caratteristiche dell'intestazione  */
table.Table thead th{
	font-size: 8pt;
	background: #fff2df;
	background: -moz-linear-gradient(top, #fff2df 0%, #d9ad7c 66%, #a2836e 100%);
	background: -webkit-linear-gradient(top, #fff2df 0%, #d9ad7c 66%, #a2836e 100%);
	background: linear-gradient(to bottom, #a2836e 0%, #a2836e 66%, #a2836e 100%);
	border-bottom: 0px solid #444444;
	text-align: center;
}
/* Caratteristiche generali delle colonne */
table.Table td {
	border: 1.5px solid #674d3c;
	padding: 1px 1px;
	font-size: 12px;
}
/* Caratteristiche della prima colonna*/
table.Table td:first-child {
	text-align: center;
	width: 5mm;
	font-size: 12px;
}
/* Caratteristiche della seconda colonna notare 'first-child + td' vale anche 'nth-child(2)'*/
table.Table td:first-child + td {
	text-align: center;
	width: 20mm;
	font-size: 12px;
}
/* Caratteristiche della terza colonna notare 'first-child + td + td' vale anche 'nth-child(3)'*/
table.Table td:first-child + td + td {
	text-align: center;
	font-size: 8pt;
	width: 50mm;
}
/* Caratteristiche delle colonne successive notare 'nth-child(even)'*/
table.Table td:nth-child(even) {
	text-align: center;
	width: 50mm;
}
/* Caratteristiche delle */
table.Table th {
	color: #fff2df;
	border: 1.5px solid #674d3c;
	padding: 1px 1px;
}
/* Caratteristiche generiche del corpo dell'html*/
table.Table tbody td {
	font-size: 8pt;
}
table.Table tr:nth-child(even){
	background: #d9ad7c;
}
/* Caratteristiche del div entro cui sta l'immagine*/
div {
	font-family: Arial, Helvetica, sans-serif;
	font-size: 15pt; color: #674d3c;
	text-align: left;
	line-height: 1.5;
}`
```
come si può notare la larghezza **width** delle colonne e la larghezza della tabella sono espresse in mm e questo è veramente utile per produrre impaginazioni precise.
↑[torna su](#HTML-and-CSS )↑

# 4. Dati di esempio
* [Arial fixed (mm)](./script-css/css/Arial%20fixed.css)
* [Black](./script-css/css/Black.css)
* [Comicgreen](./script-css/css/Comicgreen.css)
* [Grey](./script-css/css/Grey.css)

↑[torna su](#HTML-and-CSS )↑
# 5. Videotutorial
[![](https://img.youtube.com/vi/reoXJ7Pmk-I/0.jpg)](https://youtu.be/reoXJ7Pmk-I "HTML with CSS generator")

↑[torna su](#HTML-and-CSS )↑

# 6. Ringraziamenti
[QGIS.org](https://www.qgis.org/it/site/) - [divtable.com](https://divtable.com/table-styler/) - [Totò Fiandaca](https://pigrecoinfinito.com/) - A. Cusano


↑[torna su](#HTML-and-CSS )↑


# Заголовок уровня 1
Это обычная строка 1234567890  
тест синхронизации  
Это обычная строка 1234567890

## Заголовок уровня 2
Это обычная строка 1234567890  
Это обычная строка 1234567890  
хххх  
  
  
  


### Заголовок уровня 3
Это обычная строка 1234567890  
Это обычная строка 1234567890
#### Заголовок уровня 4
Это обычная строка 1234567890  
Это обычная строка 1234567890
##### Заголовок уровня 5
Это обычная строка 1234567890  
Это обычная строка 1234567890
###### Заголовок уровня 6
Это обычная строка 1234567890  
Это обычная строка 1234567890
####### Заголовок уровня 7
Это обычная строка 1234567890  
Это обычная строка 1234567890
######## Заголовок уровня 8
Это обычная строка 1234567890  
Это обычная строка 1234567890



## Лаба с кодовым названием RUDN-QGIS-3D
Порядок создания **3D-модели** на *небольшой* участок местности со зданиями и внедренными 3D-моделями объектов в QGIS и Qgis2threejs


========== 001 =================================

### **Порядок создания 3D-модели на небольшой  участок местности со зданиями и внедренными 3D-моделями объектов в QGIS и Qgis2threejs**

#### **1) Подготовительная часть**



#### Надстрочные знаки: km<sup>2</sup>. Подстрочные знаки: CO<sub>2</sub>

Here is a famous formula два доллара: $$E=mc^2$$.


Here is a famous formula один доллар: $E=mc^2$.




Создайте копию файла «Заготовка Проекта 3D.qgs», расположенного в корне папки «RUDN-QGIS-3D» с учебными материалами.

Переименуйте его, например, «**Проект 3D - Часть 2 - со зданиями.qgs**» и откройте этот проект в QGIS.

В панели Слои переместите слой «Здания - для второй части работы» на самый верх и включите его видимость.

Добавьте в проект вашу DEM (цифровую модель рельефа). Это файл с расширением **\*.tif**.

В панели Слои переместите слой с DEM в самый низ и отключите его видимость.



---------------------


| sdfdsf | fdgfdfd | ddddd   | ggggg   |
|--------|---------|---------|---------|
| 324    | 5435435 | 4435435 | 6757657 |


Это пример переноса строки (разрыв) внутри одного абзаца. Сейчас будет двойной пробел.  
Он успешно отрабатывается Writage. А вот обратный слеш, он\
Writage тоже отрабатывается. Зато он отрабатывается в GitHub.

А это уже новый абзац.

\----------------------------------------------------


Ниже `начинается многострочный` блок кода

    <!doctype html>
    <html>
        <head>
            <!-- Заголовок документа -->
        </head>
        <body>
            <!-- Тело документа -->
        </body>
    </html>

Блок кода завершился

---------------------
- - - - - - - - -

$$\phi_{n}(\kappa) = \frac{1}{4\pi^{2}\kappa^{2}}\int_{0}^{\infty}\frac{\sin(\kappa R)}{\kappa R}\frac{\partial}{\partial R}\left\lbrack R^{2}\frac{\partial D_{n}(R)}{\partial R} \right\rbrack\, dR$$


********
* * * * *

Длинный блок кода  

```html

<br> &nbsp;&nbsp; <img src="https://www.rudn.ru/u/www/images/for_smi_image/logo_rudn_eng.png" width=160>
    <p style="font-size: 16px; color: #0079c1; text-indent: 5px; margin-top: 5px;">
<b> &nbsp;&nbsp;&nbsp;&nbsp; 3D-геопортал окрестностей Махачкалы </b> </p>

```

---------------------
---------------------

**КАРТА**  
<script src="https://embed.github.com/view/geojson/benbalter/dc-wifi-social/master/bars.geojson?height=300&width=500"></script>
  
---------------------
---------------------
  
***Использование GeoJSON***  
Например, можно создать простую карту:  
```geojson
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "id": 1,
      "properties": {
        "ID": 0
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
              [-90,35],
              [-90,30],
              [-85,30],
              [-85,35],
              [-90,35]
          ]
        ]
      }
    }
  ]
}
```

---------------------
---------------------
Блок ниже оформлен просто как "Цитирование текста":  

> ## Why write a program to do that?
> 
> Note that you can easily manually count the number of bacteria colonies shown
> in the morphometric example above. Why should we learn how to write a Python
> program to do a task we could easily perform with our own eyes? There are at
> least two reasons to learn how to perform tasks like these with Python and
> skimage:
> 
> 1. What if there are many more bacteria colonies in the Petri dish? For 
> 	example, suppose the image looked like this:

---------------------
---------------------


<!-- details - это тэг html. Без атрибута "open" по умолчанию свернуто -->

<details open><summary>CLICK ME - пример сворачиваемого/разворачиваемого раздела</summary>

### Так можно скрыть что угодно, даже код!
```ruby
   puts "Hello World"
```
и вообще, как понимаю, все, что угодно :)
</details>


---------------------
---------------------

<details><summary><h3>CLICK ME - пример сворачиваемого/разворачиваемого раздела</h3></summary>

<h3>Тесты А.В.Орловского</h3>
Так можно скрыть что угодно, даже код!  
и вообще, как понимаю, все, что угодно :)

</details>

---------------------
---------------------


<table style="border: 2px solid #104E8B; background-color:#CCC;">
    <tr>
        <td style="border: 1px solid #ff0000; background-color:#CCC;">
    
<details><summary><h3>CLICK ME - пример сворачиваемого/разворачиваемого раздела</h3></summary>
    <h3>Тесты А.В.Орловского</h3>
           Так можно скрыть что угодно, даже код! <br>
           79797545235465765777987987987 <br>
           79797545235465765777987987987 <br>
           и вообще, как понимаю, все, что угодно :) <br>
           и вообще, как понимаю, все, что угодно :) <br>

</details>

</td></tr></table>



---------------------
---------------------



<!-- ===================================================================================================================== -->


<p style="letter-spacing: 4.5px">Lorem ipsum </p>
<p style="letter-spacing: -2pt; line-height:25pt"> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. </p>



<font color="#1f33b4ff">Синий текст</font>
<br>
<font face="Courier New" size="8" color="green"><b>Это мой текст!</b></font>




<h1>Моя подборка примеров блоков HTML-кода</h1>


<br>
<h2 style="font-size: 2.2em; font-family: monospace; color: #1a9835ff">Тесты А.В.Орловского</h2>


<h3>Это пример вставки ЗЩ в свою HTML-страницу с использованием iframe</h3>
<p>А это правильные рекомендации: You can use the height and width attributes to specify the size of the iframe:</p>
<iframe src="http://umap.openstreetmap.fr/ru/map/anonymous-edit/520224:cfEjyfnEYo7wlFFITRK3W5R8R4Y"  style="border:2px solid red; height:200px; width:100%; margin-left:100px;"
       >Почему-то текст здесь не на что не влияет, но и не виден???</iframe>

<br>
<br>
<br>
<h3>Это пример вставки гиперссылки, как картинки и логически связанной с ней подписью:</h3>
<!-- Нашел его здесь https://netology-code.github.io/guides/wm-cheat-sheet -->



<br>
<h3>Это пример использования аббревиатур:</h3>
<!-- Нашел его здесь https://webref.ru/course/html-content/inline-semantics -->
<p>
  Я только что купил <abbr title="Compact Disc">CD</abbr>.
</p>


<br>
<h3>Это пример строчной цитаты (кавычки):</h3>
<!-- Нашел его здесь https://webref.ru/course/html-content/inline-semantics -->
<!-- <blockquote> является блочным элементом, у него есть строчная версия <q> -->
<p>
  Он сказал <q>Привет, мир</q> и просто ушёл.
</p>






<br><br><br>
<p>ххххххххххххххх Это как бы нижний элемент у меня на странице ххххххххххххххх</p>
<br><br><br>








<div class="footer">
        &copy; 2004 Foo Corporation
</div>


* элемент маркированного списка
- ещё один элемент ненумерованного списка
+ буллеты элементов могут быть разными

1. Элемент нумерованного списка
2. Элемент №2 того же списка
9. Элемент №3 списка — элементы нумеруются по порядку, цифра в начале строки не имеет значения







Добавьте в интерфейс QGIS «**Панель координат**», включив ее через основное меню:  
«Вид Панели инструментов Панель координат».  
*(в версиях QGIS новее 3.16 эта панель называется «Дополнительные инструменты оцифровки»).*

**2) Установка дополнительных модулей, необходимых для работы**
  
  
  
  
Установите в QGIS следующие модули:

![Значок плагина](media/977f827765e8d405656bcab2fc5d340e.png) **Memory Layer Saver**

Модуль позволяет <font color="#1f33b4ff"><b>сделать имеющиеся</b></font> в проекте временные векторные слои постоянными, сохраняя их в отдельный файл с расширением \*.mldata и именем, как у самого проекта.  
*Файл с сохраненными временными слоями создается в момент сохранения проекта в том же месте,*
*где расположен файл проекта.*  
Никаких кнопок или меню в интерфейс QGIS модуль не добавляет.
<https://plugins.qgis.org/plugins/MemoryLayerSaver>






![Значок плагина](media/95d4ee9f405c998cb38ba3ca519ab00c.png) **Geometry Shapes**

Плагин позволяет рисовать основные геометрические фигуры в том числе с заданными пользователем размерами.

Возможные варианты: прямоугольники, квадраты, овалы и круги.

*Используйте клавишу «Shift», чтобы создавать идеальные квадраты и круги.*

Интегрируется как дополнительная кнопка в панель «Инструменты оцифровки».

Подробности смотрите по ссылкам:

<https://plugins.qgis.org/plugins/GeometryShapes>

<https://github.com/pvandegeer/GeometryShapes>

![Logo of QuickOSM](media/dec4e5ea9f1409053317e3ed98abfd3e.jpeg) **QuickOSM**

Позволяет загружать в QGIS данные OSM, выполняя пользовательские запросы к Overpass.

*Специальный синтаксический анализатор позволяет увидеть все доступные ключи OSM в QGIS.*

*Вы также можете открывать локальные файлы OSM или PBF.*

Подробности смотрите по ссылкам:

<https://plugins.qgis.org/plugins/QuickOSM>

[**https://docs.qgis.org/3.16/ru/docs/training_manual/qgis_plugins/plugin_examples.html\#basic-fa-the-quickosm-plugin**](https://docs.qgis.org/3.16/ru/docs/training_manual/qgis_plugins/plugin_examples.html#basic-fa-the-quickosm-plugin)

<https://docs.3liz.org/QuickOSM>

<https://github.com/3liz/QuickOSM>

**3) Выбор для создаваемой 3D-модели участка с эффектными зданиями**

С помощью слоя «Здания - для второй части работы» в пределах границ вашей DEM найдите наиболее крупный населенный пункт и выберите в нем территорию, на которой будут присутствовать наиболее эффектные в архитектурном плане здания, для которых имеется информация об их высоте.

**Справочно:**

*В слое «Здания - для второй части работы» представлена информация обо всех имеющихся (оцифрованных на данный момент) в OpenStreetMap (OSM) зданиях.*

*Здания отображаются на карте при масштабе* **1:34 123** *и крупнее серой заливкой с черной обводкой. А при увеличении масштаба карты до* **1:17 061** *и крупнее, здания, высота которых по внесенной в OSM информации превышает 5 метров ( \> 5 m ), начнут отображаться красным цветом с указанием (подписью на здании) значения высоты в метрах.*

*Здания для которых указана высота менее 5 метров включительно ( =\< 5 m ) или для которых информация о высоте отсутствует, будут по-прежнему отображаться серой заливкой с черной обводкой.*

Для удобства и наглядности, при окончательном выборе необходимого участка задайте

в основном окне QGIS значение масштаба для карты равное **1:15 000**.

Для этого в строке состояния *(расположена в самом низу окна QGIS)* в пункте «Масштаб» введите в самом окошке, отображающем значения масштаба, «**15000**» и выйдите из окошка.

**4) Создание ГИС-слоя границ создаваемой 3D-модели**

Откройте меню «Слой Создать слой Новый временный слой».

В появившемся меню задайте **Имя слоя** (например «Границы 3D-модели»),

а для параметра «**Тип геометрии**» выберите из ниспадающего меню значение «**Полигон**».

Остальные параметры оставьте без изменений.

![Alt-текст](media/2e33def7eb29834675e189eec30d04d0.png "Мой Заголовок изображения")

Задав необходимые опции, нажмите кнопку «**ОК**».

Выберите в панели «Инструменты оцифровки» кнопку ![](media/c64c479104fe419c060f33ba64c39b54.png)(Draw rectangle geometry).

Удерживая нажатой клавишу «Shift» нарисуйте на карте квадрат желаемого размера и, после появления меню «Set size (метры)»

![](media/a6370fe89c7468bc99dd84783a8ccaee.png)

уточните размеры квадрата, задав его желаемые размеры в метрах, и нажмите кнопку «**ОК**».

Для удобства и наглядности, измените стиль содержащего квадрат слоя на «**Без заливки**».

Выберите в панели инструментов «Панель координат» кнопку ![](media/297677fd2b744b99c6609ef46cbee723.png)(Переместить объекты).

Переместите с помощью это инструмента созданный вами квадрат в наиболее удачное по вашему мнению место (позицию/локацию).

Сохраните изменения в слое с границами создаваемой 3D-модели и выйдите из режима его правки через контекстное меню к слою.

Сохраните и сам QGIS-проект.

**5) Загрузка в QGIS-проект векторного слоя зданий из OpenStreetMap**

Откройте панель «**Инструменты анализа**» через меню «**Анализ данных**» «**Панель инструментов**»

![](media/6ff3354428fdd90f6241fc0c429c9970.png)

или воспользуйтесь кнопкой ![](media/bdf719fb0835b920dfc8eaa1a377132e.png), или нажмите комбинацию клавиш «Ctrl + Alt + T».

Введите в окне поиска алгоритмов «**OSM**»

![](media/738a46b12530532efea5cf03d63b489e.png)

и откройте алгоритм «**Download OSM data from a query in an extent**», сделав двойной щелчок мышью на его названии.

В открывшемся окне алгоритма для опции **«Ключ по умолчанию для всех ключей [необязательно]»** задайте значение «**building**».

Для опции «Покрытие» нажмите соответствующую кнопку с многоточием, выберите из появившегося списка вариант «**Рассчитать из слоя**», а затем выберите созданный вами слой границ для 3D-модели. После этого в окошке опции «Покрытие» появятся значения соответствующих координат.

Для сохранения результата (векторного слоя со зданиями) на компьютере, нажмите кнопку  
с многоточием и выберите из появившегося списка вариант «**Сохранить в файл …**».

Данные будут сохраняться в ГИС-формате **\*.gpkg** (GeoPackage).

Задайте имя для целевого файла как, например, «Здания».

![](media/09ca256a1eac1a55b62d1de8e176d7c4.png)

Задав необходимые опции, нажмите кнопку «**ОК**» и дождитесь появления нового слоя (загруженного из OSM слоя зданий) в панели «Слои».

Нужный для работы полигональный слой будет иметь название «**Здания_multipolygons**».

Возможно, что в QGIS-проект загрузятся дополнительные слои:

\- точечный слой «Здания_points» и

\- линейный слой «Здания_lines».

Они вам **не потребуются**. **Удалите их** из QGIS-проекта.

Переименуйте слой «Здания_multipolygons» на «Здания» и

переместите его в панели «Слои» на самый верх.

Обязательно сохраните сам QGIS-проект.

С большой вероятностью может оказаться, что контуры некоторых зданий будут выходить  
за пределы границ, определенных вами для создаваемой 3D-модели.

*Например:*

![](media/c0eb8c486d53bea524d81a7af18e427f.png)

Такие здания *(их 3D-геометрии)* на финальной 3D-модели будут либо выходить за пределы вашей 3D-модели, как бы «торча» из общей модели и повисая в пространстве.

![](media/cedeea44f5b71f2f48034777e2627bbf.png)


<p style="text-align: center;"><img src="https://raw.githubusercontent.com/Alexander-Orlovsky/RUDN-QGIS-3D/main/media/cedeea44f5b71f2f48034777e2627bbf.png" alt="Нет фото" style="width:40%; border:3px solid #ff00ff;"></p>


Либо (если включена опция «Clip geometries») окажутся «вертикально разрезанными»  
по линии границы вашей 3D-модели и будут выглядеть не вполне естественно для зданий. При этом такие «разрезы» зданий будут находиться на самой границе 3D-модели, придавая ей несколько неопрятный (неэстетичный) вид.

<center>
<img src="https://raw.githubusercontent.com/Alexander-Orlovsky/RUDN-QGIS-3D/main/media/1a339ac828e14319ec51534d14ff4aef.png" alt="Нет фото" style="width:1400px; height:300px; border:3px solid #00ffff;">
</center>

Поэтому удалите такие «лишние» здания из вашего слоя «Здания».

К таким «лишним» зданиям целесообразно отнести не только те, которые пересекают границу вашей 3D-модели, но и те, которые находятся слишком близко к ее краю.

Для этого выделите в панели «Слои» слой «Здания».

Активизируйте инструмент ![](media/a9905548ce6ba6003e797e9aa3ec4fdf.png) (Выбрать объекты в прямоугольнике или точке).

С его помощью выделите все здания, которые вы посчитаете целесообразным удалить.

*Выделенные объекты окрашиваются в желтый цвет.*

*Использование клавиш «Shift» и «Ctrl» позволит сделать процесс выделения более гибким, позволяя добавлять/исключать объекты к/из текущей выборки.*

*За дополнительной информацией о способах выделения объектов на карте вручную обратитесь к соответствующему разделу Документации QGIS по* [*ссылке*](https://docs.qgis.org/3.16/ru/docs/user_manual/introduction/general_tools.html?#selecting-manually-on-the-map-canvas)*.*

*Обратите особое внимание на возможность использования клавиши «Alt», позволяющей выбирать объекты, которые будут полностью находиться в пределах фигуры выделения.*

Вернуть случайно сброшенное выделение можно через меню:

«Правка Выделить Вернуть выделение».

В случае необходимости снять все сделанные выделения можно нажав кнопку ![](media/b30f241c7124518edc03987404f6d902.png).

После того, как вы выделите все здания, которые хотите удалить, откройте в панели «Слои» контекстное меню к слою «Здания» и активируйте для него «Режим правки».

Для удаления из слоя выделенных вами зданий, нажмите кнопку ![](media/98eb8fd0121ce3c3962f90c62dc5ae3e.png) в интерфейсе QGIS

или клавишу «Delete» на клавиатуре.

Деактивируйте «Режим правки» слоя «Здания», сохранив внесенные в него изменения.

**6) Создание 3D-модели самого ландшафта (без зданий)**

В панели «Слои» откройте контекстное меню к слою «Границы 3D-модели» и выполните действие «Увеличить до слоя».

Отключите видимость всех слоев, кроме слоя «**Космоснимки Google**».

Запустите модуль Qgis2threejs, нажав кнопку ![D:\\ORL\\Внешние_диски\\YandexDisk\\Скриншоты\\2019-12-08_16-20-43.png](media/9f83ec45662cf243f75e6e596d91db9d.png) в панели инструментов интерфейса QGIS.

В открывшемся окне «**Qgis2threejs Exporter**» в панели «**Layers**» включите (активируйте) слой вашей цифровой модели рельефа (DEM) (в моем примере это «n56_e038_1arc_v3»):

![](media/3e58188aa862654ac2eb56ddf5975a66.png)

В «Qgis2threejs Exporter» щелкните правой клавишей мыши по имени слоя вашей DEM и выберите в открывшемся контекстном меню пункт «**Properties...**».

На закладке «**Main**» появившегося окна задайте (выставьте) следующие опции:

![](media/ecdf60589137893064c068dec2ee8030.png)

Перейдите на закладку «**Others**» и задайте (выставьте) следующие опции:

![](media/5df29c7cdd388ac735d7a84046c46f08.png)

Самостоятельно подберите такое значение для опции «Altitude of bottom» (оно определяет высоту боковых сторон 3D-модели), чтобы модель выглядела изящно и эстетично.

Задав необходимые опции, нажмите последовательно клавиши «**Применить**» и «**ОК**».

Откройте в «Qgis2threejs Exporter» меню «**Scene** **Scene Settings...**» и в появившемся окне задайте (введите) следующие опции:

![](media/a93d36f20fa28f248f1b15e81e647502.png)

Оставьте значение для опции «**Z exaggeration**» (преувеличение) равным «**1.0**».

В блоке «**Base Extent**» выберите опцию/метод «**Fixed extent**», нажмите кнопку «**Select…**» и выберите вариант «**Use Layer Extent…**» (использовать охват слоя).

В появившемся окошке выберите из ниспадающего меню «**Границы 3D-модели**»:

![](media/4f091420d96a39db3c30ef3489d1fb7c.png)

Задав указанные опции, нажмите последовательно клавиши «**ОК**».

**7) Добавление в 3D-модель зданий и настройка их отображения**

В окне «Qgis2threejs Exporter» в панели «Layers» включите (активируйте) слой «**Здания**»:

![](media/909fa80ae195fbef48026834ddc681ee.png)

В «Qgis2threejs Exporter» щелкните правой клавишей мыши по имени слоя «Здания»

и выберите в открывшемся контекстном меню пункт «**Properties...**».

На закладке «**Main**» появившегося окна задайте (выставьте) следующие опции:

![](media/8fff36ef970b64dd718d1be07503c48c.png)

Задав указанные опции, нажмите клавишу «**ОК**».

В результате вы получите 3D-модель с объемными зданиями, возвышающимися над рельефом на одинаковую высоту в 30 м *(Вертикальная сторона 3D-объектов зданий задана в 50 м. При этом, для исключения эффекта висящих над земной поверхностью углов зданий, основания зданий опущены на 20 м ниже земной поверхности)*.

Сделайте 3D-модель более реалистичной, используя имеющуюся для некоторых зданий в таблице атрибутов слоя информацию об их этажности.

*Информация о количестве этажей зданий хранится в поле «***building:levels***» таблицы атрибутов загруженного из OSM слоя контуров зданий.*

Для этого для опции «**Height**» в блоке «**Geometry**» вместо фиксированного значения «50» скопируйте и вставьте следующее выражение:

CASE

WHEN "building:levels" IS NULL THEN ( 30 + 20 )

ELSE "building:levels" \* 4 + 20

END

Сделать для зданий без высоты некоторое варьирование с помощью «randf»

WHEN "building:levels" IS NULL THEN ( 30 \* rand(90, 110)/100 + 20 )

В этом выражении высота одного этажа принята равной 4 м.

Для зданий информация о количестве этажей которых в таблице атрибутов отсутствует,

величина их возвышения на земной поверхностью определено в 30 м.

|  ![](media/a4c893492b0e16ca304b41c7b408cc13.png) **Описание на Wiki OSM** Интересные подробности о том, как OpenStreetMap представляется информация о зданиях, а также о числе этажей здания, расположенных над поверхностью земли, смотрите по ссылкам ниже: **RU:Key:building:**  <https://wiki.openstreetmap.org/wiki/RU:Key:building?uselang=ru> **RU:Key:building:levels** <https://wiki.openstreetmap.org/wiki/RU:Key:building:levels?uselang=ru>  |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Измените цвет зданий на карте в основном окне QGIS, выполнив классификацию для слоя «Здания» по какому-либо логичному для данного случая полю значений, представленному в таблице атрибутов слоя.

Поля в таблице атрибутов слоя «Здания» имеют тип «String» (Текст).

Поэтому для классификации воспользуйтесь методом стилизации «Уникальные значения».

Откройте панель настройки стиля и измените метод стилизации с «Обычный знак» на «Уникальные значения». Для опции «Значение» выберите подходящее поле, например,

«**building:levels**» и какой-либо двух- и более цветный градиент для опции «Цветовой ряд».

Затем нажмите кнопку «Классифицировать».

Теперь выполните классификацию зданий по их этажности из самого модуля Qgis2threejs.

Для этого для зданий в опции «**Color**» в блоке «**Material**» вместо варианта «Feature style» выберите из ниспадающего списка «**Expression**», а в появившееся ниже окошко скопируйте и вставьте следующее выражение:

**CASE**

**WHEN** "building:levels" **\>** 5 **THEN** color_rgb**(**0**,** 255**,** 0**)** -- высокие

**WHEN** "building:levels" **\<=** 5 **THEN** color_rgb**(**0**,** 0**,** 255**)** -- низкие

**ELSE** color_rgb**(**255**,** 0**,** 0**)** -- информация о количестве этажей отсутствует

**END**

Измените представленные в выражении значения на более подходящие для создаваемой вами 3D-модели (учитывая, в том числе, особенности выбранного вами участка местности).

==============================================

Добавьте деревья

Добавьте стрелку Севера

Добавьте колонтитулы

Создайте анимацию

Увеличьте точность DEM и разрешение

Экспортирование 3D-модели в html-веб-страницу

**Опубликуйте созданную вами 3D-модель в Интернет**

![](media/b5e5d933e72f23f1721d2b4acc4a8c80.png)

**Экспортируйте вашу 3D-модель в обменный формат glTF**

![](media/4867c943503509601dd33a2a2eb8dfbb.png)


    
    
====================================================================================================================


