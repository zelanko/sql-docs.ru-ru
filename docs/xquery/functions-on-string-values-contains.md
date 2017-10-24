---
title: "Функция CONTAINS (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- contains function (XQuery)
- fn:contains function
ms.assetid: 2c88c015-04fc-429b-84b2-835596a28b65
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 025d47883976e0cf17ef9435d7bf127677a7b5b1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-string-values---contains"></a>Строковые функции — содержит
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение типа xs: Boolean, указывающее, является ли значение *$arg1* содержит строковое значение, определяемое *$arg2*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:contains ($arg1 as xs:string?, $arg2 as xs:string?) as xs:boolean?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg1*  
 Строка для проверки.  
  
 *$arg2*  
 Подстрока для поиска.  
  
## <a name="remarks"></a>Замечания  
 Если значение *$arg2* является строкой нулевой длины, функция возвращает **True**. Если значение *$arg1* является строкой нулевой длины и значение *$arg2* не является строкой нулевой длины, функция возвращает **False**.  
  
 Если значение *$arg1* или *$arg2* представляет собой пустую последовательность, аргумент интерпретируется как строка нулевой длины.  
  
 Функция contains() использует параметры сортировки кодовых точек Юникода языка XQuery по умолчанию для сравнения строк.  
  
 Искомой подстроки, указанной для *$arg2* должно быть меньше или равно 4 000 символов. Если указано значение больше, чем 4 000 символов, возникнет динамическое условие ошибки и функция contains() возвращает пустую последовательность вместо логического значения **True** или **False**. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не вызывает динамические ошибки в выражениях XQuery.  
  
 Для получения сравнения без учета регистра, [верхнего регистра](../xquery/functions-on-string-values-upper-case.md) или можно использовать функции в нижнем регистре.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных и, в некоторых случаях, от URI-кода пространства имен по умолчанию для функций. Дополнительные сведения см. в подразделе «XQuery функции учитывают суррогаты» раздела [критические изменения в функциях ядра СУБД в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). См. также [уровень совместимости инструкции ALTER DATABASE &#40; Transact-SQL &#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа xml в базе данных AdventureWorks.  
  
### <a name="a-using-the-contains-xquery-function-to-search-for-a-specific-character-string"></a>A. Использование функции contains() языка XQuery для поиска указанной строки символов  
 В следующем запросе выполняется поиск продуктов, сводное описание которых содержат слово «Aerodynamic». Для таких продуктов запрос возвращает идентификатор и элемент <`Summary`>.  
  
```  
--The product model description document uses  
--namespaces. The WHERE clause uses the exit()  
--method of the xml data type. Inside the exit method,  
--the XQuery contains()function is used to  
--determine whether the <Summary> text contains the word  
--Aerodynamic.   
  
USE AdventureWorks  
GO  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
      <Prod>  
         { /pd:ProductDescription/@ProductModelID }  
         { /pd:ProductDescription/pd:Summary }  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
   /pd:ProductDescription/pd:Summary//text()  
    [contains(., "Aerodynamic")]') = 1  
```  
  
 Результаты  
  
 `ProductModelID Result`  
  
 `-------------- ---------`  
  
 `28     <Prod ProductModelID="28">`  
  
 `<pd:Summary xmlns:pd=`  
  
 `"http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">`  
  
 `A TRUE multi-sport bike that offers streamlined riding and`  
  
 `a revolutionary design. Aerodynamic design lets you ride with`  
  
 `the pros, and the gearing will conquer hilly roads.</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  

