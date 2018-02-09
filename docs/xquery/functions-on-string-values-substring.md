---
title: "substring, функция (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- substring function [XQuery]
- fn:substring function
ms.assetid: 2b3b8651-de51-46dc-af82-c86c45eac871
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ae71eb26e93c65f853c5d1c842a1835cf40d866
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="functions-on-string-values---substring"></a>Строковые функции - подстроки
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает часть значение *$sourceString*, начиная с позиции, указываемой параметром значение *$startingLoc,* и продолжает число символов, определяется значением из *$ Длина*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc  as as xs:decimal?) as xs:string?  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?,  
                          $length as xs:decimal?) as xs:string?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$sourceString*  
 Исходная строка.  
  
 *$startingLoc*  
 Начальная позиция в исходной строке, с которой начинается подстрока. Если это значение отрицательно или равно нулю, символы возвращаются с начала строки. Если это значение превышает длину *$sourceString*, возвращается строка нулевой длины.  
  
 *$length*  
 Количество получаемых символов [дополнительно]. Если не указан, он возвращает все символы из местоположения, указанного в *$startingLoc* до конца строки.  
  
## <a name="remarks"></a>Remarks  
 Версия этой функции с тремя аргументами возвращает символы строки `$sourceString`, позиции которых `$p` удовлетворяют следующим условиям:  
  
 `fn:round($startingLoc) <= $p < fn:round($startingLoc) + fn:round($length)`  
  
 Значение *$length* может быть больше, чем количество символов в значении *$sourceString* после начальной позиции. В этом случае подстрока возвращает символы до конца *$sourceString*.  
  
 Первый символ строки расположен в позиции 1.  
  
 Если значение *$sourceString* представляет собой пустую последовательность, она обрабатывается как строка нулевой длины. В противном случае, если параметр *$startingLoc* или *$length* представляет собой пустую последовательность, возвращается пустая последовательность.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных и, в некоторых случаях, от URI-кода пространства имен по умолчанию для функций. Дополнительные сведения см. в подразделе «XQuery функции учитывают суррогаты» раздела [критические изменения в функциях ядра СУБД в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). См. также [уровень совместимости инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 SQL Server требует *$startingLoc* и *параметры $length* имели тип xs: decimal вместо xs: double.  
  
 SQL Server позволяет *$startingLoc* и *$length* быть пустую последовательность, потому что пустая последовательность может быть результатом динамических ошибок с ().  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** -столбцов в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных.  
  
### <a name="a-using-the-substring-xquery-function-to-retrieve-partial-summary-product-model-descriptions"></a>A. Использование функции XQuery substring() для получения частичного резюме о модели продукта  
 Этот запрос получает первые 50 символов строки, описывающей модель продукта, элемент <`Summary`> документа.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Prod>{ substring(string((/pd:ProductDescription/pd:Summary)[1]), 1, 50) }</Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('/pd:ProductDescription')  = 1;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **String()** функция возвращает строковое значение <`Summary`> элемент. Эту функцию необходимо использовать, потому что элемент <`Summary`> содержит как текст, так и вложенные элементы (элементы в формате html), которые нужно пропустить и вернуть весь текст.  
  
-   **Substring()** функция возвращает первые 50 символов из строкового значения, получаемого по **string()**.  
  
 Частичный результат:  
  
```  
ProductModelID Result  
-------------- ----------------------------------------------------  
19      <Prod>Our top-of-the-line competition mountain bike.</Prod>   
23      <Prod>Suitable for any type of riding, on or off-roa</Prod>  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
