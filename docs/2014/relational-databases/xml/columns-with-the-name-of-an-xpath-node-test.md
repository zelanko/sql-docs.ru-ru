---
title: Столбцы с именем XPath-функции проверки узла | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d28289cf2d0fa0319b0005828e9d1923a05a62bb
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888830"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>Столбцы с именем XPath-функции проверки узла
  Если имя столбца является одной из XPath-функций проверки узла, сопоставление содержимого производится, как указано в следующей таблице. Когда имя столбца является XPath-функцией проверки узла, содержимое сопоставляется с соответствующим узлом. Если используется тип SQL столбца `xml`, будет возвращена ошибка.  
  
|Имя столбца|Поведение|  
|-----------------|--------------|  
|text()|Строковое значение столбца с именем text() добавляется в качестве текстового узла.|  
|comment()|Строковое значение столбца с именем text() добавляется в качестве комментария XML.|  
|node()|Для столбца с именем node() результат аналогичен результату, получаемому для столбца с символом-шаблоном (*) в качестве имени.|  
|processing-instruction(name)|Строковое значение столбца с именем инструкции по обработке добавляется в качестве значения инструкции для целевого имени инструкции по обработке.|  
  
 В следующем запросе показано использование проверочных узлов в качестве имен столбцов. При этом текстовые узлы и комментарии добавляются в результирующий XML-документ.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Результат:  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>См. также  
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)  
  
  
