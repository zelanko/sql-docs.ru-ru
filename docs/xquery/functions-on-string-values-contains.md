---
title: Contains, функция (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- contains function (XQuery)
- fn:contains function
ms.assetid: 2c88c015-04fc-429b-84b2-835596a28b65
author: rothja
ms.author: jroth
ms.openlocfilehash: 54b3603c18d814276d700a220fbee5e16ed77502
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899029"
---
# <a name="functions-on-string-values---contains"></a>Функции со строковыми значениями — contains
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение типа xs: Boolean, указывающее, содержит ли значение *$arg 1* строковое значение, заданное *$arg 2*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:contains ($arg1 as xs:string?, $arg2 as xs:string?) as xs:boolean?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg 1*  
 Строка для проверки.  
  
 *$arg 2*  
 Подстрока для поиска.  
  
## <a name="remarks"></a>Remarks  
 Если значение *$arg 2* является строкой нулевой длины, функция возвращает **значение true**. Если значение *$arg 1* является строкой нулевой длины, а значение *$arg 2* не является строкой нулевой длины, функция возвращает **значение false**.  
  
 Если значение *$arg 1* или *$arg 2* является пустой последовательностью, аргумент рассматривается как строка нулевой длины.  
  
 Функция contains() использует параметры сортировки кодовых точек Юникода языка XQuery по умолчанию для сравнения строк.  
  
 Значение подстроки, указанное для *$arg 2* , должно быть меньше 4000 символов или равно ему. Если указанное значение превышает 4000 символов, возникает динамическое условие ошибки, а функция contains () возвращает пустую последовательность вместо логического значения **true** или **false**. 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не вызывает динамические ошибки в выражениях XQuery.  
  
 Чтобы получить возможность сравнения без учета регистра, можно использовать функции [верхнего](../xquery/functions-on-string-values-upper-case.md) или нижнего регистра.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных и, в некоторых случаях, от URI-кода пространства имен по умолчанию для функций. Дополнительные сведения см. в разделе "функции XQuery, поддерживающие суррогаты" в разделе [критические изменения ядро СУБД функций в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). См. также раздел [уровень совместимости ALTER database &#40;&#41;Transact-SQL](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Параметры сортировки и поддержка Юникода](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа XML в базе данных AdventureWorks.  
  
### <a name="a-using-the-contains-xquery-function-to-search-for-a-specific-character-string"></a>A. Использование функции contains() языка XQuery для поиска указанной строки символов  
 В следующем запросе выполняется поиск продуктов, сводное описание которых содержат слово «Aerodynamic». Запрос возвращает ProductID и элемент> <`Summary` для таких продуктов.  
  
```  
--The product model description document uses  
--namespaces. The WHERE clause uses the exit()  
--method of the xml data type. Inside the exit method,  
--the XQuery contains()function is used to  
--determine whether the <Summary> text contains the word  
--Aerodynamic.   
  
USE AdventureWorks  
GO  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
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
  
 `"https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">`  
  
 `A TRUE multi-sport bike that offers streamlined riding and`  
  
 `a revolutionary design. Aerodynamic design lets you ride with`  
  
 `the pros, and the gearing will conquer hilly roads.</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
