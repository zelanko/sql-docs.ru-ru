---
title: Типы данных XPath (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b490a0f4876f911923ed0429f33d332b96768792
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63131345"
---
# <a name="xpath-data-types-sqlxml-40"></a>Типы данных XPath (SQLXML 4.0)
  Набор типов данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath и XML Schema (XSD) сильно отличается. Например, в XPath отсутствуют целочисленные типы данных и тип данных для обозначения даты, а в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и XSD таких типов множество. Типы данных XSD определяют время с точностью до наносекунды, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только до одной трехсотой доли секунды. Поэтому не всегда возможно сопоставить один тип другому. Дополнительные сведения о сопоставлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных с типами данных XSD, см. в разделе [приведение типов данных и заметка SQL: DataType &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XPath есть три типа данных: `string`, `number`, и `boolean`. Тип данных `number` — это всегда тип двойной точности с плавающей запятой, соответствующий стандарту IEEE 754. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` Тип данных лучше всего соответствует XPath `number`. Однако `float(53)` не совсем соответствует IEEE 754. В частности, этот тип не содержит ни значения NaN (не число), ни значения бесконечности. Попытка преобразовать нечисловую строку в тип `number` и попытка деления на ноль вызывают ошибки.  
  
## <a name="xpath-conversions"></a>Преобразования в XPath  
 При использовании запроса XPath, например, `OrderDetail[@UnitPrice > "10.0"]`, явные и неявные преобразования типов данных могут различными неочевидными способами изменить значение запроса. Поэтому важно знать, как реализована система типов данных в XPath. Спецификация языка XPath, язык XML Path (XPath) версии 1.0 консорциума W3C Proposed Recommendation 8 октября 1999 года, можно найти на веб-сайте W3C по http://www.w3.org/TR/1999/PR-xpath-19991008.html.  
  
 Операторы XPath делятся на четыре категории:  
  
-   Логические операторы (и, или)  
  
-   Реляционные операторы (\<, >, \<=, > =)  
  
-   Операторы равенства (=, !=)  
  
-   Арифметические операторы (+, -, *, div, mod)  
  
 Операторы разных категорий по-разному преобразуют операнды. При необходимости операторы XPath неявно преобразуют операнды. Арифметические операторы преобразуют операнды к типу `number`, и результатом их выполнения является число. Логические операторы преобразуют операнды к типу `boolean`, и результатом их выполнения является логическое значение. Результатом выполнения реляционных операторов и операторов равенства является логическое значение. Однако правила преобразования, которыми пользуются операторы, зависят от первоначальных типов операндов, как показано в таблице.  
  
|Операнд|Реляционный оператор|Оператор равенства|  
|-------------|-------------------------|-----------------------|  
|Оба операнда представляют собой наборы узлов.|Значение TRUE, если и только если в первом наборе узлов есть такой узел и во втором наборе узлов есть такой узел, что сравнение их значений `string` вернет значение TRUE.|То же.|  
|Один — набор узлов, другой — `string`.|Значение TRUE, если и только если в наборе узлов есть такой узел, который после преобразования в `number` при сравнении с объектом типа `string`, преобразованным в тип `number`, вернет значение TRUE.|Значение TRUE, если и только в том случае, когда в наборе узлов есть такой узел, который после преобразования в `string` при сравнении с `string` вернет значение TRUE.|  
|Один — набор узлов, другой — `number`.|Значение TRUE, если и только в том случае, когда в наборе узлов есть такой узел, который после преобразования в `number` при сравнении с `number` вернет значение TRUE.|То же.|  
|Один — набор узлов, другой — `boolean`.|Значение TRUE, если и только если в наборе узлов есть такой узел, который после преобразования в `boolean`, а затем в `number` при сравнении с объектом типа `boolean`, преобразованным в тип `number`, вернет значение TRUE.|Значение TRUE, если и только в том случае, когда в наборе узлов есть такой узел, который после преобразования в `boolean` при сравнении с `boolean` вернет значение TRUE.|  
|Ни один из них не представляет собой набор узлов.|Преобразует оба операнда к типу `number`, а затем сравнивает их.|Преобразует оба операнда к одному типу, а затем сравнивает их. Преобразует к типу `boolean`, если хотя бы один из операндов принадлежит к типу `boolean`, и к типу `number`, если хотя бы один из операндов принадлежит к типу `number`; в противном случае преобразует к типу `string`.|  
  
> [!NOTE]  
>  Поскольку реляционные операторы XPath всегда преобразуют операнды к типу `number`, сравнение типов `string` невозможно. Чтобы включить Сравнение дат, SQL Server 2000 предлагает следующее изменение спецификации XPath: Когда Реляционный оператор сравнивает `string` для `string`, node-set `string`, или строковое значение набор узлов строковыми значениями — набор узлов, `string` сравнения (не `number` сравнения) выполняется.  
  
## <a name="node-set-conversions"></a>Преобразования наборов узлов  
 Преобразования наборов узлов не всегда интуитивно понятны. Чтобы преобразовать набор узлов в тип `string`, берется строковое значение только первого узла набора. Чтобы преобразовать набор узлов к типу `number`, он сначала преобразуется в тип `string`, а затем значение типа `string` преобразуется в тип `number`. Чтобы преобразовать набор узлов к типу `boolean`, производится его проверка на существование.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не производит выборку по положению в наборах узлов — например, запрос XPath `Customer[3]` указывает на третьего заказчика; такой тип выборки по положению не поддерживается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поэтому преобразования набора узлов в тип `string` или в тип `number`, согласно спецификации XPath, не реализованы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует семантику «любой» там, где спецификация XPath использует семантику «первый». Например, основанный на спецификации XPath консорциума W3C, запрос XPath `Order[OrderDetail/@UnitPrice > 10.0]` выберет заказы с первым **OrderDetail** с **UnitPrice** превышающая 10.0. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот запрос XPath выберет заказы с любым **OrderDetail** с **UnitPrice** превышающая 10.0.  
  
 Преобразование к типу `boolean` проводит проверку на существование, поэтому запрос XPath `Products[@Discontinued=true()]` эквивалентен выражению SQL "Products.Discontinued is not null", а не выражению SQL "Products.Discontinued = 1". Чтобы запрос был эквивалентен последнему из приведенных выражений SQL, набор узлов сначала надо преобразовать в тип, отличный от `boolean`, например, `number`. Например, `Products[number(@Discontinued) = true()]`.  
  
 Большинство операторов реализовано так, что они возвращают TRUE, если их результат равен TRUE хотя бы для одного (любого) узла набора, поэтому они возвращают FALSE, если набор узлов пуст. Таким образом, если набор узлов A пуст, оба оператора `A = B` и `A != B` вернут FALSE, а `not(A=B)` и `not(A!=B)` — TRUE.  
  
 Обычно атрибут или элемент, сопоставленный столбцу, существует, если значение этого столбца в базе данных не равно `null`. Элементы, сопоставляемые со строками, существуют, если есть хотя бы один из их дочерних элементов.  
  
> [!NOTE]  
>  Элементы с аннотацией `is-constant` существуют всегда. Следовательно, предикаты XPath нельзя использовать для элементов, помеченных как `is-constant`.  
  
 При преобразовании набора узлов в тип `string` или `number` его тип XDR, если таковой указан в аннотируемой схеме, анализируется и при необходимости служит основой для решения о преобразовании типов.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Сопоставление типов данных XDR типам данных XPath  
 Тип данных XPath узла является производным от типа данных XDR в схему, как показано в следующей таблице (узел **EmployeeID** иллюстративных целях).  
  
|Тип данных XDR|Эквивалентный<br /><br /> тип данных XPath|Использованное преобразование SQL Server|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|Н/Д|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|number|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|строка|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|н/д (в XPath нет типа данных, эквивалентного типу fixed14.4 XDR)|CONVERT(money, EmployeeID)|  
|date|строка|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|строка|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Преобразования даты и времени, предназначены для работы ли значение хранится в базе данных с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` тип данных или `string`. Обратите внимание, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` тип данных не использует `timezone` и имеет меньшую точность, чем XML `time` тип данных. Чтобы включить тип данных `timezone` или более высокую точность, следует хранить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием типа `string`.  
  
 При преобразовании узла из типа данных XDR в тип данных XPath иногда требуются дополнительные преобразования (из одного типа XPath в другой тип XPath). В качестве примера рассмотрим следующий запрос XPath:  
  
```  
(@m + 3) = 4  
```  
  
 Если @m имеет `fixed14.4` тип данных XDR, преобразование из типа данных XDR в тип данных выполняется с помощью XPath:  
  
```  
CONVERT(money, m)  
```  
  
 В данном случае узел `m` преобразуется из типа `fixed14.4` в тип `money`. Однако для прибавления 3 требуется дополнительное преобразование:  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 Выражение XPath вычисляется следующим образом:  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 Как показано в следующей таблице, это то же самое преобразование, которое применялось для других выражений XPath (например, литералов или составных выражений).  
  
||||||  
|-|-|-|-|-|  
||Х неизвестен|X является `string`|X является `number`|X является `boolean`|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) &GT; 0|X != 0|-|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. Преобразование типа данных в запросе XPath  
 В следующем запросе XPath к аннотированной схеме XSD запрос выбирает все **сотрудника** узлов с **EmployeeID** значение E-1, где «E-» — префикс, указанный с помощью атрибута `sql:id-prefix` заметки.  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Предикат в запросе эквивалентен следующему выражению SQL:  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 Так как **EmployeeID** является одним из `id` (`idref`, `idrefs`, `nmtoken`, `nmtokens`, и т. д) тип данных значения в схеме XSD, **EmployeeID** — преобразовать в `string` с помощью описанных ранее правил преобразования типа данных XPath.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 К строке добавляется префикс «E-», а результат затем сравнивается с `N'E-1'`.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>Б. Несколько преобразований типов данных в запросе XPath  
 Рассмотрим следующий запрос XPath к аннотированной схеме XSD. `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Этот запрос XPath возвращает все  **\<OrderDetail >** элементы, удовлетворяющие предикату `@UnitPrice * @OrderQty > 98`. Если **UnitPrice** помечается `fixed14.4` типа данных в схеме с заметками, этот предикат эквивалентен выражению SQL:  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 В ходе преобразований значений в запросе XPath сначала тип данных XDR преобразуется в тип данных XPath. Так как тип данных XSD **UnitPrice** является `fixed14.4`, как описано в предыдущей таблице, это первого преобразования, который используется:  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Поскольку арифметические операторы преобразуют операнды к типу XPath `number`, применяется второе преобразование (от одного типа данных XPath к другому), в результате которого значение преобразуется к типу `float(53)` (тип `float(53)` близок к типу данных XPath `number`):  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 При условии, что **OrderQty** атрибут имеет тип данных XSD не **OrderQty** преобразуется в `number` тип данных XPath за один:  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 Подобным же образом значение 98 преобразуется к типу данных XPath `number`:  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Если используемый в схеме тип данных XSD несовместим с базовым типом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных или нужное преобразование типа данных XPath невозможно выполнить, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может вернуть ошибку. Например если **EmployeeID** помечается атрибутом `id-prefix` заметки, XPath `Employee[@EmployeeID=1]` вызовет ошибку, поскольку **EmployeeID** имеет `id-prefix` заметки и не может быть преобразован `number`.  
  
  
