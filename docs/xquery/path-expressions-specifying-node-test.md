---
title: "Установка проверки узла в шаге выражения пути | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- node test [XQuery]
ms.assetid: ffe27a4c-fdf3-4c66-94f1-7e955a36cadd
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3f9fece26e607005cca982be1963a9ca8a53a632
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="path-expressions---specifying-node-test"></a>Выражения пути — установка проверки узла
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Шаг оси в выражении пути содержит следующие компоненты:  
  
-   [Оси](../xquery/path-expressions-specifying-axis.md)  
  
-   Проверка узла  
  
-   [Ноль или более необязательных квалификаторов шага)](../xquery/path-expressions-specifying-predicates.md)  
  
 Дополнительные сведения см. в разделе [выражения пути &#40; XQuery &#41; ](../xquery/path-expressions-xquery.md).  
  
 Проверка узла является условием и вторым компонентом шага оси в выражении пути. Этому условию должны удовлетворять все узлы, выбранные на шаге. Для выражения пути `/child::ProductDescription` проверкой узла является `ProductDescription`. Этот шаг получает только потомки элементных узлов с именем ProductDescription.  
  
 В условии проверки узла могут быть указаны следующие данные:  
  
-   Имя узла. Возвращаются только узлы с заданным именем, относящиеся к основному узлу.  
  
-   Тип узла. Возвращаются только узлы заданного типа.  
  
> [!NOTE]  
>  Имена узлов, заданные в выражениях пути XQuery, всегда обрабатываются с учетом регистра и не подчиняются тем же правилам зависимости от параметров сортировки, что и запросы на Transact-SQL.  
  
## <a name="node-name-as-node-test"></a>Имя узла в качестве проверки узла  
 При указании имени узла в качестве проверки узла в шаге выражения пути необходимо понимать принцип основного узла. У каждой оси, потомка, родителя и атрибута есть основной узел. Например:  
  
-   Ось атрибутов может содержать только атрибуты. Поэтому узел атрибутов является основным по отношению к оси атрибутов.  
  
-   Что касается других осей - если выбранные осью узлы могут содержать элементные узлы, то элементный узел является основным для этой оси.  
  
 При указании имени узла в качестве проверки узла шаг возвращает следующие типы узлов:  
  
-   Узлы, являющиеся основными узлами оси.  
  
-   Узлы с именем, которое задано в проверке узла.  
  
 Например, рассмотрим следующее выражение пути:  
  
```  
child::ProductDescription   
```  
  
 Это одношаговое выражение задает ось `child` и имя узла `ProductDescription` в качестве проверки узла. Выражение возвращает только те узлы с именем ProductDescription, которые являются основными для дочерней оси и элементных узлов.  
  
 У выражения пути `/child::PD:ProductDescription/child::PD:Features/descendant::*,` есть три шага. Они задают дочерние оси и оси потомков. На каждом шаге имя узла задается в качестве проверки узла. Символ-шаблон (`*`) на третьем шаге задает все узлы главного узла для оси-потомка. Основной узел оси определяет тип выбранных узлов, а имя узла их отфильтровывает.  
  
 В результате при выполнении этого выражения к XML-документам каталога продуктов в **ProductModel** таблицы, он извлекает все дочерние узлы элемента \<функции > дочерний узел элемента \< ProductDescription > элемент.  
  
 Выражение пути `/child::PD:ProductDescription/attribute::ProductModelID`, состоит из двух шагов. В обоих имя узла задается в качестве проверки узла. Кроме того, в каждом шаге используется ось атрибутов. Поэтому в каждом шаге выбираются узлы основного узла оси с именем, заданным в качестве проверки узла. Таким образом, выражение возвращает **ProductModelID** узел атрибутов \<ProductDescription > узла элемента.  
  
 Как показано в следующем примере, при указании имен узлов для проверки локальное имя узла или префикс его пространства имен можно задавать с помощью символа-шаблона (*):  
  
```  
declare @x xml  
set @x = '  
<greeting xmlns="ns1">  
   <salutation>hello</salutation>  
</greeting>  
<greeting xmlns="ns2">  
   <salutation>welcome</salutation>  
</greeting>  
<farewell xmlns="ns1" />'  
select @x.query('//*:greeting')  
select @x.query('declare namespace ns="ns1"; /ns:*')  
```  
  
## <a name="node-type-as-node-test"></a>Тип узла в качестве проверки узла  
 Для запросов к типу узла, а не к элементным узлам, используется проверка типа узла. Существует четыре вида проверки типа узла, как показано в следующей таблице:  
  
|Тип узла|Возвращает|Пример|  
|---------------|-------------|-------------|  
|`comment()`|Верно для узла комментариев.|`following::comment()` выбирает все узлы комментариев, которые появляются после контекстного узла.|  
|`node()`|Верно для всех узлов.|`preceding::node()` выбирает все узлы, которые появляются перед контекстным узлом.|  
|`processing-instruction()`|Верно для узла инструкций по обработке.|`self::processing instruction()` выбирает все узлы инструкций по обработке в контекстном узле.|  
|`text()`|Верно для текстового узла.|`child::text()` выбирает все текстовые узлы, являющиеся потомками контекстного узла.|  
  
 Если в качестве проверки узла задан тип узла, например text() или comment() ..., то шаг возвращает узлы заданного типа независимо от основного узла оси. Например, следующее выражение пути возвращает только потомки узла комментариев к контекстному узлу:  
  
```  
child::comment()  
```  
  
 Аналогичным образом `/child::ProductDescription/child::Features/child::comment()` извлекает комментарий дочерние узлы \<функции > дочерний узел элемента \<ProductDescription > узла элемента.  
  
## <a name="examples"></a>Примеры  
 В следующем примере сравниваются имена и типы узлов.  
  
### <a name="a-results-of-specifying-the-node-name-and-the-node-type-as-node-tests-in-a-path-expression"></a>A. Результаты указания имени и типа узла в качестве проверки узла в выражении пути  
 В следующем примере простой XML-документ присваивается **xml** переменной типа. К этому документу выполняется запрос с помощью разных выражений пути. Результаты сравниваются.  
  
```  
declare @x xml  
set @x='  
<a>  
 <b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
 </b>  
</a>'  
select @x.query('  
/child::a/child::b/descendant::*  
')  
```  
  
 Это выражение запрашивает элементные узлы-потомки элементного узла `<b>`.  
  
 Звездочка (`*`) в проверке узла задает символ-шаблон для имени узла. В качестве элементного узла выступает основной узел оси-потомка. Поэтому выражение возвращает все элементные узлы-потомки элементного узла `<b>`. То есть возвращаются элементные узлы `<c>` и `<d>`, как показано в следующем результате:  
  
```  
<c>text2  
     <d>text3</d>  
</c>  
<d>text3</d>  
```  
  
 Если вместо оси-потомка задать ось descendent-or-self, то возвращается контекстный узел и его потомки.  
  
```  
/child::a/child::b/descendant-or-self::*  
```  
  
 Это выражение возвращает элементный узел `<b>` и его элементные узлы-потомки. При возвращении узлов-потомков основной узел оси descendant-or-self, тип элементного узла, определяет виды возвращаемых узлов.  
  
 Результат:  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
  
<c>text2  
     <d>text3</d>  
</c>  
  
<d>text3</d>   
```  
  
 В предыдущем выражении в качестве имени узла использовался символ-шаблон. Вместо него можно использовать функцию `node()`, как показано в следующем выражении:  
  
```  
/child::a/child::b/descendant::node()  
```  
  
 Поскольку `node()` является типом узла, будут получены все узлы оси-потомка. Результат:  
  
```  
text1  
<c>text2  
     <d>text3</d>  
</c>  
text2  
<d>text3</d>  
text3  
```  
  
 Если в качестве проверки узла задать ось descendant-or-self и `node()`, то будут получены все потомки, элементы и текстовые узлы, а также контекстный узел, элемент `<b>`.  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
text1  
<c>text2  
     <d>text3</d>  
</c>  
text2  
<d>text3</d>  
text3  
```  
  
### <a name="b-specifying-a-node-name-in-the-node-test"></a>Б. Указание имени узла при проверке узла  
 В следующем примере в качестве проверки узла во всех выражениях пути задается имя узла. В результате все выражения возвращают узлы основного узла оси, имена которых были указаны при проверке узлов.  
  
 Следующее выражение запроса возвращает элемент <`Warranty`> из XML-документа каталога продуктов, который хранится в таблице `Production.ProductModel`:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::PD:ProductDescription/child::PD:Features/child::wm:Warranty  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Ключевое слово `namespace` в прологе XQuery определяет префикс, который используется в теле запроса. Дополнительные сведения о прологе XQuery см. в разделе [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) .  
  
-   Все три шага в выражении пути задают дочернюю ось и имя узла в качестве проверки узла.  
  
-   Необязательный квалификатор шага не задан ни в одном шаге выражения.  
  
 Запрос возвращает дочерние элементы <`Warranty`> дочернего элемента <`Features`> элемента <`ProductDescription`>.  
  
 Результат:  
  
```  
<wm:Warranty xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
  <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
  <wm:Description>parts and labor</wm:Description>  
</wm:Warranty>     
```  
  
 В следующем запросе выражение пути задает символ-шаблон (`*`) в проверке узла.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::PD:ProductDescription/child::PD:Features/child::*  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Этот символ-шаблон задан для имени узла. Таким образом, запрос возвращает все элементные узлы-потомки элементного узла-потомка <`Features`> элементного узла <`ProductDescription`>.  
  
 Следующий запрос похож на предыдущий, за исключением того, что вместе с символом-шаблоном задано пространство имен. В результате возвращаются все элементные узлы-потомки в этом пространстве имен. Обратите внимание, что элемент <`Features`> может содержать элементы из разных пространств имен.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::PD:ProductDescription/child::PD:Features/child::wm:*  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Этот символ-шаблон можно использовать в качестве префикса пространства имен, как показано в следующем запросе:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::PD:ProductDescription/child::PD:Features/child::*:Maintenance  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Запрос возвращает элементные узлы-потомки <`Maintenance`> из всех пространств имен XML-документа каталога продуктов.  
  
### <a name="c-specifying-node-kind-in-the-node-test"></a>В. Указание типа узла при проверке узла  
 В следующем примере в качестве проверки узла во всех выражениях пути задается тип узла. В результате все выражения возвращают узлы того типа, который задан в проверке узла.  
  
 В следующем запросе выражение пути в третьем шаге задает тип узла.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::PD:ProductDescription/child::PD:Features/child::text()  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 В следующем запросе указывается следующее:  
  
-   Выражение пути состоит из трех шагов, разделенных косой чертой (`/`).  
  
-   В каждом шаге задается дочерняя ось.  
  
-   Первые два шага задают имя узла в качестве проверки узла, а на третьем шаге указывается тип узла в качестве проверки узла.  
  
-   Выражение возвращает текстовые узлы-потомки <`Features`> дочернего элемента элементного узла <`ProductDescription`>.  
  
 Возвращаются только текстовые узлы. Результат:  
  
```  
These are the product highlights.   
```  
  
 Следующий запрос возвращает дочерние узлы комментариев к элементу <`ProductDescription`>:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::PD:ProductDescription/child::comment()  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Второй шаг задает тип узла в качестве проверки узла.  
  
-   В результате выражение возвращает дочерние узлы комментариев к элементным узлам <`ProductDescription`>.  
  
 Результат:  
  
```  
<!-- add one or more of these elements... one for each specific product in this product model -->  
<!-- add any tags in <specifications> -->      
```  
  
 Следующий запрос получает узлы обработки инструкций верхнего уровня:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::processing-instruction()  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Результат:  
  
```  
<?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>   
```  
  
 Проверке запроса `processing-instruction()` в качестве параметров можно передавать строковые литералы. В этом случае запрос возвращает инструкции по обработке, для которых значение атрибута имени является строковым литералом, заданным аргументом.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
 /child::processing-instruction("xml-stylesheet")  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Ниже приводятся особые ограничения.  
  
-   Проверки узлов расширенного типа SequenceType не поддерживаются.  
  
-   Формат вида «инструкция_по_обработке(имя)» не поддерживается. Имя следует указывать в кавычках.  
  
  
