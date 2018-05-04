---
title: Инструкция SELECT (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SELECT
dev_langs:
- kbMDX
helpviewer_keywords:
- SELECT statement [MDX]
- cubes [Analysis Services], SELECT statement
ms.assetid: c0a57214-aa3f-44ce-a369-660c69746f34
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: fc495e44fd9c2bc49ba54afbb17cc48a5a855ac6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-manipulation---select"></a>Управление данными MDX - Выбор
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Извлекает данные из заданного куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
[ WITH <SELECT WITH clause>   
   [ , <SELECT WITH clause>...n ]   
]   
SELECT   
     [ *   
    | ( <SELECT query axis clause>   
                  [ , <SELECT query axis clause>,...n ]   
            )   
            ]  
FROM   
   <SELECT subcube clause>   
      [ <SELECT slicer axis clause> ]  
      [ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
     ( CELL CALCULATION <CREATE CELL CALCULATION body clause> )   
   | ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>)   
   | ( SET <CREATE SET body clause>)  
   | ( MEASURE = <measure body clause> )  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression  
   [ <SELECT dimension property list clause> ]   
      ON   
            Integer_Expression   
       | AXIS(Integer)   
       | COLUMNS   
       | ROWS   
       | PAGES   
       | SECTIONS   
       | CHAPTERS   
  
<SELECT subcube clause> ::=  
      Cube_Name   
   | [NON VISUAL] (SELECT   
                  [ *   
       | ( <SELECT query axis clause> [ ,   
           <SELECT query axis clause>,...n ] )   
         ]   
            FROM   
         <SELECT subcube clause>   
         <SELECT slicer axis clause> )  
  
<SELECT slicer axis clause> ::=   
      WHERE Tuple_Expression  
  
<SELECT cell property list clause> ::=   
   [ CELL ] PROPERTIES CellProperty_Name   
      [ , CellProperty_Name,...n ]  
  
<SELECT dimension property list clause> ::=  
   [DIMENSION] PROPERTIES   
      (DimensionProperty_Name   
         [,DimensionProperty_Name,...n ] )   
    | (LevelProperty_Name   
         [, LevelProperty_Name,...n ] )   
    | (MemberProperty_Name   
         [, MemberProperty_Name,...n ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Целочисленный*  
 Целое число между 0 и 127.  
  
 *Cube_Name*  
 Допустимая строка, представляющая имя куба.  
  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
 *CellProperty_Name*  
 Допустимая строка, представляющая свойство ячейки.  
  
 *DimensionProperty_Name*  
 Допустимая строка, представляющая свойство измерения.  
  
 *LevelProperty_Name*  
 Допустимая строка, представляющая свойство уровня.  
  
 *MemberProperty_Name*  
 Допустимая строка, представляющая свойство элемента.  
  
## <a name="remarks"></a>Замечания  
 В выражении `<SELECT slicer axis clause>` должны содержаться элементы измерений и иерархий, отличающиеся от указанных в заданных выражениях `<SELECT query axis clause>`.  
  
 Если в заданных выражениях `<SELECT query axis clause>` и значении `<SELECT slicer axis clause>` атрибут куба пропущен, то к оси среза неявно добавляется элемент атрибута по умолчанию.  
  
 Параметр NON VISUAL в инструкции подзапроса выборки позволяет отфильтровать элементы во время хранения верных итогов вместо отфильтрованных. Это позволяет выполнить запрос для первых десяти продаж (люди/продукты/регионы) и получить истинный итог продаж для всех запрашиваемых элементов, а не общий итог для первых десяти возвращаемых. Дополнительные сведения см. в примерах ниже.  
  
 Вычисляемые элементы могут быть включены в \<предложение осей запроса SELECT > каждый раз, когда было открыто соединение с помощью параметра строки подключения *вложенные запросы = 1*; в разделе [поддерживаемые свойства XMLA &#40; XML для Аналитики&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) и <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> для использования параметра. Пример приведен для вычисляемых элементов в подзапросах выборки.  
  
## <a name="autoexists"></a>Автоматическая проверка существования  
 Если два или более атрибута измерения используются в инструкции SELECT, службы Analysis Services оценивают эти атрибуты, чтобы обеспечить, что элементы этих атрибутов правильно ограничены и соответствуют критериям остальных атрибутов. Например, предположим, что идет работа с атрибутами измерения «Geography». Если существует выражение, возвращающее все элементы атрибута «Город», и другое выражение, ограничивающее элементы атрибута «Страна» всеми странами Европы, то элементы атрибута «Город» будут ограничены только городами, расположенным в странах Европы. Эта характеристика служб Analysis Services называется автоматической проверкой существования и применима только к атрибутам, находящимся в одном измерении. Автоматическая проверка существования применима только к атрибутам, находящимся в одном измерении, потому что пытается предотвратить включение записей измерения, не включенных в одно выражение с атрибутом, в другое выражение с атрибутом. Автоматическую проверку существования можно также воспринимать как результат пересечения различных выражений с атрибутом по записям измерения. См. следующий пример:  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 Полученный результирующий набор выглядит следующим образом:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Велосипед Mountain-200**|**$ 14 356 699,36**|**$ 19 012,71**|**0,13 %**|  
|**Road-250**|**$ 9 377 457,68**|**$ 4 032,47**|**0.04%**|  
|**Mountain-100**|**$ 8 568 958,27**|**$ 139 393,27**|**1,63 %**|  
|**Road-650**|**$ 7 442 141,81**|**$ 39 698,30**|**0,53 %**|  
|**Touring-1000**|**$ 6 723 794,29**|**$ 166 144,17**|**2,47 %**|  
|**Road-550-W**|**$ 3 668 383,88**|**$ 1 901,97**|**0,05 %**|  
|**Road-350-W**|**$ 3 665 932,31**|**$ 20 946,50**|**0,57 %**|  
|**HL Mountain Frame**|**$ 3 365 069,27**|**$ 174,11**|**0,01 %**|  
|**Road-150**|**$ 2 363 805,16**|**$0,00**|**0,00%**|  
|**Touring-3000**|**$ 2 046 508,26**|**$ 79 582,15**|**3,89 %**|  
  
 Полученный набор продуктов выглядит так же, как и Preferred10Products; проверяем набор Preferred10Products:  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 Согласно полученным результатам наборы Top10SellingProducts и Preferred10Products совпадают:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Велосипед Mountain-200**|**$ 14 356 699,36**|**$ 19 012,71**|**0,13 %**|  
|**Road-250**|**$ 9 377 457,68**|**$ 4 032,47**|**0.04%**|  
|**Mountain-100**|**$ 8 568 958,27**|**$ 139 393,27**|**1,63 %**|  
|**Road-650**|**$ 7 442 141,81**|**$ 39 698,30**|**0,53 %**|  
|**Touring-1000**|**$ 6 723 794,29**|**$ 166 144,17**|**2,47 %**|  
|**Road-550-W**|**$ 3 668 383,88**|**$ 1 901,97**|**0,05 %**|  
|**Road-350-W**|**$ 3 665 932,31**|**$ 20 946,50**|**0,57 %**|  
|**HL Mountain Frame**|**$ 3 365 069,27**|**$ 174,11**|**0,01 %**|  
|**Road-150**|**$ 2 363 805,16**|**$0,00**|**0,00%**|  
|**Touring-3000**|**$ 2 046 508,26**|**$ 79 582,15**|**3,89 %**|  
  
 В предыдущих примерах были созданы два набора: один — как вычисляемое выражение, другой — как константное выражение. В этих примерах демонстрируются другие особенности автоматической проверки существования.  
  
 Автоматическую проверку существования можно применить к выражениям глубоко или поверхностно. Значение по умолчанию — глубоко. Следующий пример демонстрирует концепцию глубокой автоматической проверки существования. В примере набор Top10SellingProducts фильтруется по атрибуту [Product].[Product Line] для попадающих в группу [Mountain]. Обратите внимание, что оба атрибута (срез и ось) принадлежат одному измерению ([Product]).  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 Создает следующий результирующий набор:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Велосипед Mountain-200**|**$ 14 356 699,36**|**$ 19 012,71**|**0,13 %**|  
|**Mountain-100**|**$ 8 568 958,27**|**$ 139 393,27**|**1,63 %**|  
|**HL Mountain Frame**|**$ 3 365 069,27**|**$ 174,11**|**0,01 %**|  
|**Mountain-300**|**$ 1 907 249,38**|**$ 876,95**|**0,05 %**|  
|**Mountain-500**|**$ 1 067 327,31**|**$ 17 266,09**|**1,62 %**|  
|**Mountain-400-W**|**$ 592 450,05**|**$ 303,49**|**0,05 %**|  
|**LL Mountain Frame**|**$ 521 864,42**|**$ 252,41**|**0,05 %**|  
|**ML Mountain Frame-W**|**$ 482 953,16**|**$ 206,95**|**0.04%**|  
|**ML Mountain Frame**|**$ 343 785,29**|**$ 161,82**|**0,05 %**|  
|**Женские шорты Mountain**|**$ 260 304,09**|**$ 6 675,56**|**2,56 %**|  
  
 Предыдущий результирующий набор содержит в списке Top10SellingProducts семь новых элементов, а Mountain-200, Mountain-100 и HL Mountain Frame переместились в начало списка. В предыдущем результирующем наборе эти три значения перемешивались с другими элементами.  
  
 Это называется глубокой автоматической проверкой существования, так как набор Top10SellingProducts оценивается на соответствие условиям срезов в запросе. Глубокая автоматическая проверка существования означает, что все выражения будут оцениваться для обнаружения наибольшего пространства из возможных после применения выражений выделения среза, выражений подзапроса по оси и т. д.  
  
 Однако может возникнуть необходимость проведения анализа Top10SellingProducts как эквивалента Preferred10Products, как в следующем примере:  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 Создает следующий результирующий набор:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Велосипед Mountain-200**|**$ 14 356 699,36**|**$ 19 012,71**|**0,13 %**|  
|**Mountain-100**|**$ 8 568 958,27**|**$ 139 393,27**|**1,63 %**|  
|**HL Mountain Frame**|**$ 3 365 069,27**|**$ 174,11**|**0,01 %**|  
  
 В результатах, приведенных выше, срез дает результат, содержащий только те продукты из набора Preferred10Products, которые являются частью группы [Mountain] атрибута [Product].[Product Line], потому что Preferred10Products является константным выражением.  
  
 Результирующий набор можно воспринимать как поверхностную автоматическую проверку существования. Это связано с тем, что выражение оценивается перед предложением среза. В предыдущем примере выражение было константным для демонстрации особенностей в целях представления о концепции.  
  
 Поведение автоматической проверки существования может изменяться на уровне сеанса при помощи свойства **Autoexists** строки подключения. В следующих примерах открывается новый сеанс и добавляется свойство *Autoexists=3* в строку подключения. Для выполнения примера необходимо создать новое соединение. После установки соединения с параметром автоматической проверки существования (Autoexist) эта проверка будет выполняться до самого закрытия соединения.  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 Следующий результирующий набор демонстрирует поведение поверхностной автоматической проверки существования.  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Велосипед Mountain-200**|**$ 14 356 699,36**|**$ 19 012,71**|**0,13 %**|  
|**Mountain-100**|**$ 8 568 958,27**|**$ 139 393,27**|**1,63 %**|  
|**HL Mountain Frame**|**$ 3 365 069,27**|**$ 174,11**|**0,01 %**|  
  
 Поведение автоматической проверки существования может изменяться с помощью параметра AUTOEXISTS = [1 | 2 | 3] параметр в строке подключения; в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) и <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> для использования параметра.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, суммарный за первые восемь месяцев календарного 2003, содержащихся в `Date` измерения, от **Adventure Works** куба.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Чтобы понять **NON VISUAL** следующий пример — запрос [Adventure Works] для получения значений [Reseller Sales Amount] в таблице, где категории продуктов являются столбцами, а типы торговых посредников являются строками. Обратите внимание, что итоги даны и для продуктов, и для торговых посредников.  
  
 Рассмотрим следующую инструкцию SELECT.  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Она выдает следующие результаты.  
  
|||||||  
|-|-|-|-|-|-|  
||**All Products**|**Accessories**|**Bikes**|**Clothing**|**Components**|  
|**All Resellers**|**$ 80 450 596,98**|**$ 571 297,93**|**$ 66 302 381,56**|**$ 1 777 840,84**|**$ 11 799 076,66**|  
|**Specialty Bike Shop**|**$ 6 756 166,18**|**$ 65 125,48**|**$ 6 080 117,73**|**$ 252 933,91**|**$ 357 989,07**|  
|**Value Added Reseller**|**$ 34 967 517,33**|**$ 175 002,81**|**$ 30 892 354,33**|**$ 592 385,71**|**$ 3 307 774,48**|  
|**Warehouse**|**$ 38 726 913,48**|**$ 331 169,64**|**$ 29 329 909,50**|**$ 932 521,23**|**$ 8 133 313,11**|  
  
 Чтобы создать таблицу с данными только для продуктов Accessories и Clothing и торговых посредников Value Added Reseller и Warehouse, хранение полных итогов должно быть записано при помощи NON VISUAL следующим образом.  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Она выдает следующие результаты.  
  
|||||  
|-|-|-|-|  
||**All Products**|**Accessories**|**Clothing**|  
|**All Resellers**|**$ 80 450 596,98**|**$ 571 297,93**|**$ 1 777 840,84**|  
|**Value Added Reseller**|**$ 34 967 517,33**|**$ 175 002,81**|**$ 592 385,71**|  
|**Warehouse**|**$ 38 726 913,48**|**$ 331 169,64**|**$ 932 521,23**|  
  
 Чтобы создать таблицу, которая визуально рассчитывает итоги столбцов, а для строк приводится истинный итог всех [Category], необходимо выполнить следующий запрос.  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Обратите внимание, что NON VISUAL применяется только к [Category].  
  
 Этот запрос выдаст следующий результат.  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$ 73 694 430,80|$ 506 172,45|$ 1 524 906,93|  
|Value Added Reseller|$ 34 967 517,33|$ 175 002,81|$ 592 385,71|  
|Warehouse|$ 38 726 913,48|$ 331 169,64|$ 932 521,23|  
  
 При сравнении с предыдущими результатами можно заметить, что в строке [All Resellers] складываются отображаемые значения [Value Added Reseller] и [Warehouse], однако столбец [All Products] отображает общее значение для всех продуктов, включая те, которые не отображаются.  
  
 В следующем примере показано применение вычисляемых элементов в подзапросах выборки для фильтрации по ним. Для выполнения этого образца необходимо установить подключение с помощью параметра строки подключения *вложенные запросы = 1*.  
  
 `select Measures.allmembers on 0`  
  
 `from (`  
  
 `Select { [Measures].[Reseller Sales Amount]`  
  
 `, [Measures].[Reseller Total Product Cost]`  
  
 `, [Measures].[Reseller Gross Profit]`  
  
 `, [Measures].[Reseller Gross Profit Margin]`  
  
 `} on 0`  
  
 `from [Adventure Works]`  
  
 `)`  
  
 Этот запрос выдаст следующий результат.  
  
|||||  
|-|-|-|-|  
|Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|Reseller Gross Profit Margin|  
|$ 80 450 596,98|$79,980,114.38|$470,482.60|0.58%|  
  
## <a name="see-also"></a>См. также  
 [Ключевые понятия многомерных Выражений & #40; Службы Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Инструкции языка манипулирования данными &#40;многомерных Выражений&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Ограничение запроса с & #40; запросов и осей среза Многомерные Выражения & #41;](~/analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-restricting-the-query.md)  
  
  

