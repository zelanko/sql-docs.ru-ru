---
title: Пример Указание директивы ELEMENTXSINIL | Документация Майкрософт
description: Узнайте, как указать в SQL директиву ELEMENTXSINIL, чтобы создавать XML-элементы для значений NULL, в которых атрибут xsi:nil имеет значение true.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTXSINIL directive
ms.assetid: bbcb6f9e-a51b-4775-9795-947c9d6d758f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64e44b8f84f2ff4b908556b31b6088a6a2c77c55
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632508"
---
# <a name="example-specifying-the-elementxsinil-directive"></a>Пример Определение директивы ELEMENTXSINIL
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  При указании директивы ELEMENT для извлечения элементного XML, если столбец имеет значение NULL, соответствующий элемент не будет сформирован при режиме EXPLICIT. Можно указать директиву ELEMENTXSINIL, чтобы создать элементы со значениями NULL для элементов, у которых атрибут **xsi:nil** установлен в значение TRUE.  
  
 Следующий запрос создает XML, включающий адрес работника. Для столбцов `AddressLine2` и `City` в именах столбцов указана директива `ELEMENTXSINIL` . Это позволяет создать элемент для значений NULL в столбцах `AddressLine2` и `City` набора строк.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID  as [Employee!1!EmpID],  
       BEA.AddressID as [Employee!1!AddressID],  
       NULL        as [Address!2!AddressID],  
       NULL        as [Address!2!AddressLine1!ELEMENT],  
       NULL        as [Address!2!AddressLine2!ELEMENTXSINIL],  
       NULL        as [Address!2!City!ELEMENTXSINIL]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.BusinessEntityAddress AS BEA  
    ON E.BusinessEntityID = BEA.BusinessEntityID  
  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       BEA.AddressID,  
       A.AddressID,  
       AddressLine1,   
       AddressLine2,  
       City   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.BusinessEntityAddress AS BEA  
    ON E.BusinessEntityID = BEA.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BEA.AddressID = A.AddressID  
ORDER BY [Employee!1!EmpID],[Address!2!AddressID]  
FOR XML EXPLICIT;  
```  
  
 Частичный результат:  

```xml
<Employee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          EmpID="1"
          AddressID="249">
  <Address AddressID="249">
    <AddressLine1>4350 Minute Dr.</AddressLine1>
    <AddressLine2 xsi:nil="true" />
    <City>Minneapolis</City>
  </Address>
</Employee>
...
```
  
## <a name="see-also"></a>См. также:  
 [Использование режима EXPLICIT с предложением FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
