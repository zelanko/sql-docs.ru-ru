---
title: Автоматическая проверка существования | Документация Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 56283497-624c-45b5-8a0d-036b0e331d22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 090a7cdb4958dacdaebcdcc0db176991d6bebaa1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142704"
---
# <a name="autoexists"></a>автоматическая проверка существования
  Концепция *автоматической проверки существования* ограничивает пространство куба теми ячейками, которые фактически существуют в кубе, в противоположность тем ячейкам, которые могут существовать в результате создания всех возможных комбинаций элементов иерархии атрибута, принадлежащих одной иерархии. Это происходит потому, что элементы одной иерархии атрибута не могут существовать в одном измерении с элементами другой иерархии атрибута. Если в инструкции SELECT используются две или более иерархии атрибута одного измерения, службы Analysis Services оценивают эти атрибуты, чтобы убедиться, что элементы этих атрибутов правильно ограничены и соответствуют критериям остальных атрибутов.  
  
 Например, предположим, что идет работа с атрибутами измерения «Geography». Если существует выражение, возвращающее все элементы атрибута «City», и другое выражение, ограничивающее элементы атрибута «Country» всеми странами Европы, то элементы атрибута «City» будут ограничены только городами, расположенным в странах Европы. Такое поведение определяется характеристиками автоматической проверки существования службы Analysis Services. Автоматическая проверка существования применима только к атрибутам, находящимся в одном измерении, потому что пытается предотвратить включение записей измерения, не включенных в одно выражение с атрибутом, в другое выражение с атрибутом. Автоматическую проверку существования можно также воспринимать как результат пересечения различных выражений с атрибутом по строкам измерения.  
  
## <a name="cell-existence"></a>Существование ячейки  
 Следующие ячейки существуют всегда:  
  
-   Элемент «(Все)» любой иерархии при пересечении с элементами других иерархий в том же измерении.  
  
-   Вычисляемые элементы при пересечении с невычисляемыми одноуровневыми элементами или с родителями или потомками своих невычисляемых одноуровневых элементов.  
  
## <a name="providing-non-existing-cells"></a>Создание несуществующих ячеек  
 Несуществующая ячейка — это ячейка, создаваемая системой в ответ на запрос или вычисление, требующие ячейку, которая не существует в кубе. Например, пространство куба, содержащего иерархию атрибута «City» и иерархию атрибута «Country», принадлежащие измерению «Geography», и меру Internet Sales Amount, включает только те элементы, которые существуют друг с другом. Например, если иерархия атрибута «City» содержит элементы «New York», «London», «Paris», «Tokyo» и «Melbourne», а иерархия атрибута «Country» содержит страны «United States», «United Kingdom», «France», «Japan» и «Australia», то пространство куба не содержит ячейку на пересечении элементов «Paris» и «United States».  
  
 Запрос к несуществующим ячейкам возвращает значение NULL, то есть они не могут содержать вычисления и нельзя определить вычисления, записывающие данные в это место пространства. Например, следующая инструкция включает в себя несуществующие ячейки.  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  В следующем запросе применяется функция [Members (Set) (многомерные выражения)](/sql/mdx/members-set-mdx) для получения набора элементов иерархии атрибута Gender по оси столбцов и выполняется перекрестное соединение этого набора с заданным набором элементов из иерархии атрибута Customer по оси строк.  
  
 При выполнении предыдущего запроса ячейка на пересечении элементов [Aaron A. Allen] и [Female] отображает значение NULL. Аналогично, значение NULL отображается в ячейке на пересечении элементов [Abigail Clark] и [Male]. Эти ячейки не существуют и не могут содержать значение, но запрос может вернуть несуществующие ячейки.  
  
 При использовании функции [Crossjoin (многомерные выражения)](/sql/mdx/crossjoin-mdx) для получения перекрестного произведения элементов иерархий атрибутов из иерархий атрибутов одного измерения автоматическое существование ограничивает возвращаемые кортежи набором действительно существующих кортежей, а не возвращает все декартово произведение. Выполните следующий запрос и изучите его результаты.  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  Обратите внимание, что 0 используется для обозначения оси столбцов, это сокращение для оси(0), являющейся осью столбцов.  
  
 В предыдущем запросе возвращаются только ячейки для элементов каждой иерархии атрибута в запросе, которые существуют друг с другом. Предыдущий запрос можно записать, используя новый * variant [Crossjoin (многомерные Выражения)](/sql/mdx/crossjoin-mdx) функции.  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 Предыдущий запрос можно переписать следующим образом:  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 Значения ячеек будут совпадать, хотя метаданные в результирующем наборе будут разными. Например, в предыдущем запросе иерархия Country перемещена на ось среза (в предложении WHERE) и поэтому не представлена явно в результирующем наборе.  
  
 Каждый из перечисленных запросов демонстрирует поведение функции автоматического существования в службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="deep-and-shallow-autoexists"></a>Глубокая и поверхностная автоматические проверки существования  
 Автоматическую проверку существования можно применять к выражениям глубоко или поверхностно. `Deep Autoexists` означает, что все выражения будут оцениваться по наибольшему из возможных пространств после применения выражений выделения среза, выражений подзапроса по оси и т. д. `Shallow Autoexists` означает, что внешние выражения оцениваются перед текущим выражением и их результаты будут переданы в текущее выражение. По умолчанию выполняется глубокая автоматическая проверка существования.  
  
 Для иллюстрации различных типов автоматической проверки существования рассмотрим следующий сценарий и соответствующие примеры. В следующих примерах будут созданы два набора: один — как вычисляемое выражение, другой — как константное выражение.  
  
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
  
 Следующий пример демонстрирует концепцию глубокой автоматической проверки существования. В примере набор Top10SellingProducts фильтруется по атрибуту [Product].[Product Line] для попадающих в группу [Mountain]. Обратите внимание, что оба атрибута (срез и ось) принадлежат одному измерению ([Product]).  
  
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
  
 Приведенный выше результирующий набор содержит в списке Top10SellingProducts семь новых элементов, а Mountain-200, Mountain-100 и HL Mountain Frame переместились в начало списка. В предыдущем результирующем наборе эти три значения перемешивались с другими элементами.  
  
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
  
 Результирующий набор можно также представить как поверхностную автоматическую проверку существования. Это связано с тем, что выражение оценивается перед предложением среза. В предыдущем примере выражение было константным для демонстрации особенностей в целях представления о концепции.  
  
 Поведение автоматической проверки существования может изменяться на уровне сеанса при помощи свойства `Autoexists` строки подключения. В следующих примерах открывается новый сеанс и добавляется свойство *Autoexists=3* в строку подключения. Для выполнения примера необходимо создать новое соединение. После установки соединения с параметром автоматической проверки существования (Autoexist) эта проверка будет выполняться до самого закрытия соединения.  
  
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
  
 Поведение автоматической проверки существования может изменяться с помощью параметра AUTOEXISTS = [1 | 2 | 3] параметр в строке подключения; см. в разделе [поддерживаемые свойства XMLA &#40;XMLA&#41; ](../../xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) и <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> сведения об использовании параметра.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия многомерных выражений &#40;служб Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Пространство куба](cube-space.md)   
 [Кортежи](tuples.md)   
 [Работа с элементами, кортежами и наборами &#40;многомерных Выражений&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Визуальные и невизуальные итоги](visual-totals-and-non-visual-totals.md)   
 [Справочник по языку многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Многомерные выражения &#40;многомерных Выражений&#41; ссылки](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
