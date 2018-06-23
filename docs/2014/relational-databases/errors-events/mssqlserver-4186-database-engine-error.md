---
title: MSSQLSERVER_4186 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 4186 (Database Engine error)
ms.assetid: 1ae88554-f291-45bc-a186-6f41d9cd0fca
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 45a36655c2ee1459cae7b5240f8c928b876ae1d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191207"
---
# <a name="mssqlserver4186"></a>MSSQLSERVER_4186
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|4186|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Нельзя ссылаться на столбец «%ls.%.*ls» из предложения OUTPUT, так как определение столбца содержит вложенный запрос или ссылку на функцию, которая выполняет доступ к системным данным или данным пользователя. По умолчанию предполагается, что функция выполняет доступ к данным, если она не привязана к схеме. Рассмотрите возможность удаления вложенного запроса или функции из определения столбца либо удаления столбца из предложения OUTPUT.|  
  
## <a name="explanation"></a>Объяснение  
 Во избежание недетерминированного поведения в предложении OUTPUT запрещено ссылаться на столбец из представления или встроенной функции, возвращающей табличное значение, если этот столбец определен одним из следующих методов.  
  
-   Вложенный запрос.  
  
-   Определяемая пользователем функция, которая осуществляет или может осуществлять доступ к пользовательским или системным данным.  
  
-   Вычисляемый столбец, содержащий определяемую пользователем функцию, которая осуществляет доступ к пользовательским или системным данным в своем определении.  
  
### <a name="examples"></a>Примеры  
 **Просмотр столбца, определенного вложенным запросом**  
  
 В следующем примере создается представление, которое использует вложенный запрос в списке выбора, чтобы определить столбец `State`. После этого инструкция UPDATE ссылается на столбец `State` в предложении OUTPUT и происходит ошибка из-за вложенного запроса в списке выбора.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.V1  
AS  
    SELECT City,  
-- subquery to return the State name  
           (SELECT Name FROM Person.StateProvince AS sp   
            WHERE sp.StateProvinceID = a.StateProvinceID) AS State  
    FROM Person.Address AS a;  
GO  
--Reference the State column in the OUTPUT clause of an UPDATE statement  
UPDATE dbo.V1   
SET City = City + 'Test'   
OUTPUT deleted.City, deleted.State, inserted.City, inserted.State  
WHERE State = 'Texas';  
GO  
```  
  
 **Просмотр столбца, определенного функцией**  
  
 В следующем примере создается представление, которое использует в списке выбора скалярную функцию `dbo.ufnGetStock` доступа к данным, чтобы определить столбец `CurrentInventory`. Затем инструкция UPDATE ссылается на столбец `CurrentInventory` в предложении OUTPUT.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ReorderLevels  
AS  
    SELECT ProductID, ProductModelID, ReorderPoint,  
           dbo.ufnGetStock(ProductID) AS CurrentInventory  
    FROM Production.Product;  
GO  
  
UPDATE Production.ReorderLevels  
SET ReorderPoint += CurrentInventory  
OUTPUT deleted.ReorderPoint, deleted.CurrentInventory,  
       inserted.ReorderPoint, inserted.CurrentInventory  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
## <a name="user-action"></a>Действие пользователя  
 Ошибку 4186 можно исправить одним из следующих способов.  
  
-   Используйте соединения вместо вложенных запросов, чтобы определить столбец в представлении или функции. Например, можно перезаписать представление `dbo.V1` следующим образом.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE VIEW dbo.V1  
    AS  
        SELECT City, sp.Name AS State  
        FROM Person.Address AS a   
        JOIN Person.StateProvince AS sp   
        ON sp.StateProvinceID = a.StateProvinceID;  
    ```  
  
-   Изучите определение определяемой пользователем функции. Если функция не осуществляет доступ к пользовательским или системным данным, измените функцию, включив в нее предложение WITH SCHEMABINDING.  
  
-   Удалите столбец из предложения OUTPUT.  
  
## <a name="see-also"></a>См. также  
 [Предложение OUTPUT (Transact-SQL)](/sql/t-sql/queries/output-clause-transact-sql)  
  
  
