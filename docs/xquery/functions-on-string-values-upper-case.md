---
title: Функция upper (XQuery) | Документация Майкрософт
description: Узнайте, как использовать функцию XQuery с прописной буквой (), которая преобразует символы в их эквиваленты в верхнем регистре.
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- upper-case
- upper-case Function (XQuery)
ms.assetid: 5bd01ad2-7adf-48fb-bf42-41e200419d37
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e48fb5448284cc90a87aff88a9cf7a0304c661d
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87107228"
---
# <a name="functions-on-string-values---upper-case"></a>Функции со строковыми значениями — upper-case
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  Эта функция преобразует каждый символ в *$arg* в его эквивалент в верхнем регистре. В двоичном преобразовании регистра Microsoft Windows для кодовых точек Юникода указано, как символы преобразуются в верхний регистр. Этот стандарт отличается от сопоставления для стандарта кодовых точек Юникода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:upper-case($arg as xs:string?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
  
|Термин|Определение|  
|-|-|
|*$arg*|Строковое значение для преобразования в верхний регистр.|  
  
## <a name="remarks"></a>Комментарии  
 Если значение *$arg* пустое, возвращается строка нулевой длины.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-a-string-to-upper-case"></a>A. Преобразование строки в верхний регистр  
 Следующий пример изменяет входную строку "abcDEF! @4 " в верхний регистр.  
  
```  
DECLARE @x xml = N'abcDEF!@4';  
SELECT @x.value('fn:upper-case(/text()[1])', 'nvarchar(10)');  
```  
  
### <a name="b-search-for-a-specific-character-string"></a>Б. Поиск конкретной символьной строки  
 В этом примере показано использование функции upper-case для выполнения поиска без учета регистра.  
  
```  
USE AdventureWorks  
GO  
--WITH XMLNAMESPACES clause specifies the namespace prefix  
--to use.   
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
--The XQuery contains() function is used to determine whether  
--any of the text nodes below the <Summary> element contain  
--the word 'frame'. The upper-case() function is used to make  
--the search case-insensitive.  
  
SELECT ProductModelID, CatalogDescription.query('  
      <Prod>  
         { /pd:ProductDescription/@ProductModelID }  
         { /pd:ProductDescription/pd:Summary }  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
/pd:ProductDescription/pd:Summary//text()[  
          contains(upper-case(.), "FRAME")]')  = 1  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
 `ProductModelID Result`  
  
 `-------------- ---------`  
  
 `19     <Prod ProductModelID="19">`  
  
 `<pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike.`  
  
 `Performance-enhancing options include the innovative HL Frame,`  
  
 `super-smooth front suspension, and traction for all terrain.`  
  
 `</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
 `25     <Prod ProductModelID="25">`  
  
 `<pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">This bike is ridden by race winners. Developed with the`  
  
 `Adventure Works Cycles professional race team, it has a extremely light`  
  
 `heat-treated aluminum frame, and steering that allows precision control.`  
  
 `</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
