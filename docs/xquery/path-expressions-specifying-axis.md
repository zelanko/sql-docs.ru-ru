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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946483"
---
# <a name="path-expressions---specifying-axis"></a>Выражения пути — указание оси
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Шаг оси в выражении пути содержит следующие компоненты:  
  
-   Ось  
  
-   Объект [проверки узла](../xquery/path-expressions-specifying-node-test.md)  
  
-   [Ноль или несколько необязательных квалификаторов шага)](../xquery/path-expressions-specifying-predicates.md)  
  
 Дополнительные сведения см. в разделе [выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md).  
  
 Выполнение XQuery в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает следующие шаги оси:  
  
|Ось|Описание|  
|----------|-----------------|  
|**Дочерний**|Возвращает дочерние элементы контекстного узла.|  
|**потомка**|Возвращает всех потомков контекстного узла.|  
|**parent**|Возвращает родительский элемент контекстного узла.|  
|**Атрибут**|Возвращает атрибуты контекстного узла.|  
|**SELF**|Возвращает сам контекстный узел.|  
|**descendant-or-self**|Возвращает сам контекстный узел и всех его потомков.|  
  
 Все эти оси, за исключением **родительского** оси, являются направленными вперед осями. **Родительского** оси — обратная ось, так как он ищет в обратном направлении в иерархии документа. Например, относительное выражение пути `child::ProductDescription/child::Summary` имеет два шага, и каждый шаг указывает ось `child`. Первый шаг получает \<ProductDescription > дочерние элементы узла контекста. Для каждого \<ProductDescription > второй шаг Получает дочерний узел элемента \<Сводка > элементные узлы-потомки.  
  
 Относительное выражение пути `child::root/child::Location/attribute::LocationID` имеет три шага. Каждый из первых двух шагов указывает ось `child`, а третий этап указывает ось `attribute`. При выполнении для производственных инструкций, XML-документов в **Production.ProductModel** таблицы, выражение возвращает `LocationID` атрибут \<расположение > дочерний узел элемента \<корневой > элемент.  
  
## <a name="examples"></a>Примеры  
 Примеры запросов в этом разделе указаны по отношению к **xml** -столбцов в **AdventureWorks** базы данных.  
  
### <a name="a-specifying-a-child-axis"></a>A. Указание дочерней оси  
 Для определенной модели продукта следующий запрос извлекает \<функции > дочерние узлы элемента \<ProductDescription > узла элемента в описании каталога продукции, хранящиеся в `Production.ProductModel` таблицы.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   `query()` Метод **xml** выражение пути задает тип данных.  
  
-   Оба шага в выражении пути указывают ось `child` и имена узлов, `ProductDescription` и `Features`, в качестве проверок узлов. Сведения о проверках узла см. в разделе [указание проверки узла в шаге выражения пути](../xquery/path-expressions-specifying-node-test.md).  
  
### <a name="b-specifying-descendant-and-descendant-or-self-axes"></a>Б. Указание осей descendant или descendant-or-self  
 Следующий пример использует ось descendant, а также ось descendant-or-self. Запрос в этом примере задается для **xml** переменной типа. Экземпляр XML упрощен, чтобы было легче проиллюстрировать различие в формируемых результатах.  
  
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
  
 `/child::a/child::b/descendant::*`, то будут запрошены все потомки узла <`b`> элементного узла.  
  
 Звездочка (*) в проверке узла представляет имя узла как проверку узла. Поэтому тип основного узла оси потомков, узел-элемент, определяет типы возвращаемых узлов. Таким образом, выражение возвращает все узлы-элементы. Текстовые узлы возвращены не будут. Дополнительные сведения о типе основного узла и его связи с проверкой узла см. в разделе [указание проверки узла в шаге выражения пути](../xquery/path-expressions-specifying-node-test.md) раздела.  
  
 Узлы элемента <`c`> и <`d`> возвращаются, как показано в следующем результате:  
  
```  
<c>text2  
     <d>text3</d>  
</c>  
<d>text3</d>  
```  
  
 Если указать ось descendant-or-self вместо оси-потомка, `/child::a/child::b/descendant-or-self::*` возвращает контекстный узел, элемент <`b`> и его потомков.  
  
 Это результат:  
  
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
  
 Следующий образец запроса к **AdventureWorks** базы данных получает все элементные узлы <`Features`> дочернего элемента <`ProductDescription`> элемент:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features/descendant::*  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
### <a name="c-specifying-a-parent-axis"></a>В. Указание родительской оси  
 Следующий запрос возвращает <`Summary`> дочернего элемента <`ProductDescription`> элемент в XML-документа каталога продуктов хранится в `Production.ProductModel` таблицы.  
  
 Этот пример использует родительскую ось для возврата к родителю элемента <`Feature`> и получения <`Summary`> дочернего элемента <`ProductDescription`> элемента.  
  
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
  
 Каждый описания каталога моделей продуктов, хранящихся в **CatalogDescription** столбец **ProductModel** таблица имеет `<ProductDescription>` элемент, имеющий `ProductModelID` атрибут и `<Features>`дочерний элемент, как показано в следующем фрагменте:  
  
```  
<ProductDescription ProductModelID="..." >  
  ...  
  <Features>  
    <Feature1>...</Feature1>  
    <Feature2>...</Feature2>  
   ...  
</ProductDescription>  
```  
  
 Запрос устанавливает в инструкции FLWOR переменную-итератор, `$f`, с целью возврата дочерних элементов для элемента `<Features>`. Дополнительные сведения см. в разделе [итерация и инструкция FLWOR &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md). Для каждой характеристики предложение `return` создает XML следующего вида:  
  
```  
<Feature ProductModelID="...">...</Feature>  
<Feature ProductModelID="...">...</Feature>  
```  
  
 Чтобы добавить `ProductModelID` для каждого `<Feature`> элемент, `parent` ось:  
  
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
  
  
