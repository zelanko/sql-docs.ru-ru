---
title: "Создание представлений и хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1bc361e589dba1215781adcf951fd419b7dc806f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-3---creating-views-and-stored-procedures"></a>Занятие 2-3 - Создание представлений и хранимых процедур
После того как Мэри предоставлен доступ к базе данных **TestData** , можно создать некоторые объекты базы данных, такие как представление или хранимая процедура, а затем предоставить Мэри доступ к ним. Представление является хранимой инструкцией SELECT, а хранимая процедура представляет собой одну или более инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] , выполняемых в виде пакета.  
  
Представления запрашиваются так же, как таблицы, и не принимают параметры. Хранимые процедуры сложнее, чем представления. Хранимые процедуры содержат как входные, так и выходные параметры и могут содержать инструкции, которые управляют потоком кода, например IF и WHILE. Использование хранимых процедур для всех повторяющихся действий в базе данных является хорошим стилем программирования.  
  
В этом примере используется инструкция CREATE VIEW, чтобы создать представление, которое выбирает только два столбца в таблице **Products** . Затем с помощью инструкции CREATE PROCEDURE создается хранимая процедура, которая принимает цену в качестве параметра и возвращает только те продукты, цена которых меньше значения, указанного в качестве параметра.  
  
### <a name="to-create-a-view"></a>Создание представления  
  
1.  Выполните следующую инструкцию, создающую очень простое представление, которое выполняет инструкцию select и возвращает названия и цены продуктов пользователю.  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a>Тестирование представления  
  
1.  С представлениями обращаются так же, как с таблицами. Используйте инструкцию `SELECT` , чтобы получить доступ к представлению.  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a>Создание хранимой процедуры  
  
1.  В следующем примере создается хранимая процедура `pr_Names`с входным параметром `@VarPrice` типа `money`. Эта хранимая процедура печатает инструкцию `Products less than` , соединенную операцией сцепления с входным параметром, тип которого преобразуется из `money` в `varchar(10)` . Затем процедура выполняет инструкцию `SELECT` на представлении, передавая входной параметр в предложение `WHERE` . Возвращаются все продукты, цена которых меньше значения входного параметра.  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a>Тестирование хранимой процедуры  
  
1.  Чтобы выполнить хранимую процедуру, введите и выполните следующую инструкцию. Эта процедура должна возвратить названия двух продуктов, введенных в таблицу `Products` на занятии 1, цена которых меньше `10.00`.  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Предоставление доступа к объекту базы данных](../t-sql/lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a>См. также:  
[CREATE VIEW (Transact-SQL)](../t-sql/statements/create-view-transact-sql.md)  
[CREATE PROCEDURE (Transact-SQL)](../t-sql/statements/create-procedure-transact-sql.md)  
  
  
  

