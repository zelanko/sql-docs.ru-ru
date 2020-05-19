---
title: Столбцы, по умолчанию содержащие значение NULL | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3aaa7cc6fb40c2f600e734cb3e2250a40e15d63e
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717294"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Столбцы, по умолчанию содержащие значение NULL
  По умолчанию значение NULL в столбце сопоставляется с отсутствием атрибута, узла или элемента. Это поведение, установленное по умолчанию, может быть изменено с помощью запроса к элементно-ориентированному документу XML с использованием директивы ELEMENTS и указания ключевого слова XSINIL для добавления элементов для значений NULL, как показано в следующем запросе:  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 Ниже показан результат. Обратите внимание, что, если ключевое слово XSINIL не указано, элемент <`Middle`> будет отсутствовать.  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>См. также  
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)  
  
  
