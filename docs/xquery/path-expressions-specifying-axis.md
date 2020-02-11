---
title: Указание оси в шаге выражения пути | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- attribute axis [SQL Server]
- axis step [XQuery]
- descendant axis
- self axis
- path expressions [XQuery]
- child axis
- descendant-or-self axis
- parent axis
ms.assetid: c44fb843-0626-4496-bde0-52ca0bac0a9e
author: rothja
ms.author: jroth
ms.openlocfilehash: 07058816406ef6ac0d5a3356423e231a10ce6165
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946483"
---
# <a name="path-expressions---specifying-axis"></a>Выражения пути — указание оси
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Шаг оси в выражении пути содержит следующие компоненты:  
  
-   Ось  
  
-   [Проверка узла](../xquery/path-expressions-specifying-node-test.md)  
  
-   [Несколько необязательных квалификаторов шага (или ни одного)](../xquery/path-expressions-specifying-predicates.md)  
  
 Дополнительные сведения см. в разделе [выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md).  
  
 Выполнение XQuery в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает следующие шаги оси:  
  
|Ось|Description|  
|----------|-----------------|  
|**ребенок**|Возвращает дочерние элементы контекстного узла.|  
|**descendant**|Возвращает всех потомков контекстного узла.|  
|**источника**|Возвращает родительский элемент контекстного узла.|  
|**версию**|Возвращает атрибуты контекстного узла.|  
|**самообслуживания**|Возвращает сам контекстный узел.|  
|**потомок или-Self**|Возвращает сам контекстный узел и всех его потомков.|  
  
 Все эти оси, за исключением **родительской** оси, являются прямыми осями. **Родительская** ось — это обратная ось, так как она выполняет поиск в обратном направлении в иерархии документа. Например, относительное выражение пути `child::ProductDescription/child::Summary` имеет два шага, и каждый шаг указывает ось `child`. Первый шаг получает дочерний элемент \<ProductDescription> элемента контекстного узла. Для каждого \<узла элемента ProductDescription> второй шаг извлекает дочерние \<элементы узла сводки> элементов.  
  
 Относительное выражение пути `child::root/child::Location/attribute::LocationID` имеет три шага. Каждый из первых двух шагов указывает ось `child`, а третий этап указывает ось `attribute`. При выполнении в XML-документах с инструкциями по производству в таблице **Production. ProductModel** выражение возвращает `LocationID` атрибут \<Location> элемент element \<корневого элемента>.  
  
## <a name="examples"></a>Примеры  
 Примеры запросов в этом разделе указываются для столбцов типа **XML** в базе данных **AdventureWorks** .  
  
### <a name="a-specifying-a-child-axis"></a>A. Указание дочерней оси  
 Для конкретной модели продукта следующий запрос получает \<компоненты,> дочерние узлы узла элемента \<ProductDescription> из описания каталога продуктов, хранящегося в `Production.ProductModel` таблице.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   `query()` Метод типа данных **XML** задает выражение пути.  
  
-   Оба шага в выражении пути указывают ось `child` и имена узлов, `ProductDescription` и `Features`, в качестве проверок узлов. Дополнительные сведения о тестировании узлов см. [в разделе Указание проверки узла в шаге выражения пути](../xquery/path-expressions-specifying-node-test.md).  
  
### <a name="b-specifying-descendant-and-descendant-or-self-axes"></a>Б. Указание осей descendant или descendant-or-self  
 Следующий пример использует ось descendant, а также ось descendant-or-self. Запрос в этом примере задается для переменной типа **XML** . Экземпляр XML упрощен, чтобы было легче проиллюстрировать различие в формируемых результатах.  
  
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
declare @y xml  
set @y = @x.query('  
  /child::a/child::b  
')  
select @y  
```  
  
 В следующем результате выражение возвращает дочерний узел-элемент `<b>` для узла-элемента `<a>`:  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
```  
  
 Если в этом выражении указать ось потомков для данного выражения пути,  
  
 `/child::a/child::b/descendant::*`, запрашиваются все потомки узла <`b`> элемента.  
  
 Звездочка (*) в проверке узла представляет имя узла как проверку узла. Поэтому тип основного узла оси потомков, узел-элемент, определяет типы возвращаемых узлов. Таким образом, выражение возвращает все узлы-элементы. Текстовые узлы возвращены не будут. Дополнительные сведения о типе первичного узла и его связи с тестом узла см. [в разделе Указание проверки узла в шаге выражения пути](../xquery/path-expressions-specifying-node-test.md) .  
  
 Узлы элементов <`c`> и <`d`> возвращаются, как показано в следующем результате:  
  
```  
<c>text2  
     <d>text3</d>  
</c>  
<d>text3</d>  
```  
  
 Если вместо оси потомков указать ось-потомок, `/child::a/child::b/descendant-or-self::*` то возвращает узел контекста, элемент <`b`> и его потомков.  
  
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
  
 Следующий пример запроса к базе данных **AdventureWorks** извлекает все узлы-потомки элемента <`Features`> дочернего элемента <`ProductDescription` элемента>:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features/descendant::*  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
### <a name="c-specifying-a-parent-axis"></a>В. Указание родительской оси  
 Следующий запрос возвращает дочерний `Summary` элемент <> элемента <`ProductDescription`> в XML-документе каталога продуктов, который хранится в `Production.ProductModel` таблице.  
  
 В этом примере используется родительская ось, чтобы вернуться к родительскому элементу <`Feature`> и получить дочерний элемент <`Summary`> элемента `ProductDescription` <>.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
/child::PD:ProductDescription/child::PD:Features/parent::PD:ProductDescription/child::PD:Summary  
')  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
  
```  
  
 В этом примере запроса выражение пути использует ось `parent`. Можно переписать это выражение без родительской оси так, как показано ниже:  
  
```  
/child::PD:ProductDescription[child::PD:Features]/child::PD:Summary  
```  
  
 Более полезный пример родительской оси представлен в следующем примере.  
  
 Каждое описание каталога модели продукта, хранящееся в столбце **CatalogDescription** таблицы **ProductModel** , содержит `<ProductDescription>` элемент с `ProductModelID` атрибутом и `<Features>` дочерним элементом, как показано в следующем фрагменте кода:  
  
```  
<ProductDescription ProductModelID="..." >  
  ...  
  <Features>  
    <Feature1>...</Feature1>  
    <Feature2>...</Feature2>  
   ...  
</ProductDescription>  
```  
  
 Запрос устанавливает в инструкции FLWOR переменную-итератор, `$f`, с целью возврата дочерних элементов для элемента `<Features>`. Дополнительные сведения см. в разделе [Инструкция FLWOR и итерация &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md). Для каждой характеристики предложение `return` создает XML следующего вида:  
  
```  
<Feature ProductModelID="...">...</Feature>  
<Feature ProductModelID="...">...</Feature>  
```  
  
 Чтобы добавить элемент `ProductModelID` for each `<Feature`>, необходимо указать `parent` ось:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  for $f in /child::PD:ProductDescription/child::PD:Features/child::*  
  return  
   <Feature  
     ProductModelID="{ ($f/parent::PD:Features/parent::PD:ProductDescription/attribute::ProductModelID)[1]}" >  
          { $f }  
   </Feature>  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат:  
  
```  
<Feature ProductModelID="19">  
  <wm:Warranty   
   xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
    <wm:Description>parts and labor</wm:Description>  
  </wm:Warranty>  
</Feature>  
<Feature ProductModelID="19">  
  <wm:Maintenance   
   xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:NoOfYears>10 years</wm:NoOfYears>  
    <wm:Description>maintenance contract available through your dealer   
                  or any AdventureWorks retail store.</wm:Description>  
  </wm:Maintenance>  
</Feature>  
<Feature ProductModelID="19">  
  <p1:wheel   
   xmlns:p1="https://www.adventure-works.com/schemas/OtherFeatures">  
      High performance wheels.  
  </p1:wheel>  
</Feature>  
```  
  
 Учтите, что предикат `[1]` в выражении пути будет добавлен, чтобы гарантировать, что будет возвращено одноэлементное значение.  
  
  
