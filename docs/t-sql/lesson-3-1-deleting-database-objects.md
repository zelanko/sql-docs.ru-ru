---
title: "Удаление объектов базы данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bcd4f3254cfd6b648411ae6fb9c364fa7017913
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-3-1---deleting-database-objects"></a>Занятие 3-1-Удаление объектов базы данных
Чтобы удалить все записи, созданные при использовании учебника, достаточно удалить базу данных. Тем не менее, в данном разделе будет показано, как аннулировать любое действие, совершенное при выполнении заданий из этого учебника.  
  
### <a name="removing-permissions-and-objects"></a>Удаление разрешений и объектов  
  
1.  Перед удалением объектов необходимо убедиться, что используется нужная база данных:  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  С помощью инструкции `REVOKE` удаляется разрешение на выполнение, предоставленное `Mary` на хранимую процедуру:  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  С помощью инструкции `DROP` удаляется разрешение, предоставленное `Mary` для доступа к базе данных `TestData` :  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  С помощью инструкции `DROP` удаляется разрешение, предоставленное `Mary` для доступа к экземпляру [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  С помощью инструкции `DROP` удаляется хранимая процедура `pr_Names`:  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  С помощью инструкции `DROP` удаляется представление `vw_Names`:  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  С помощью инструкции `DELETE` удаляются все строки таблицы `Products` :  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  С помощью инструкции `DROP` удаляется таблица `Products` :  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. Базу данных `TestData` невозможно удалить во время нахождения в ней; поэтому сначала требуется переключить контекст на другую базу данных и только после этого с помощью инструкции `DROP` удалить базу данных `TestData` :  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
Это заключительный шаг учебника «Составление инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] ». Помните, что этот учебник содержит только краткий обзор и не включает описания всех параметров используемых инструкций. Для проектирования и создания эффективной структуры базы данных и настройки безопасного доступа к данным требуется более сложная база данных, чем показанная в примерах данного учебника.  
  
## <a name="return-to-sql-server-tools-portal"></a>Возвращение к порталу средств SQL Server  
[Учебник. Составление инструкций Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>См. также:  
[REVOKE (Transact-SQL)](../t-sql/statements/revoke-transact-sql.md)  
[DROP USER (Transact-SQL)](../t-sql/statements/drop-user-transact-sql.md)  
[DROP LOGIN (Transact-SQL)](../t-sql/statements/drop-login-transact-sql.md)  
[DROP PROCEDURE (Transact-SQL)](../t-sql/statements/drop-procedure-transact-sql.md)  
[DROP VIEW (Transact-SQL)](../t-sql/statements/drop-view-transact-sql.md)  
[DELETE (Transact-SQL)](../t-sql/statements/delete-transact-sql.md)  
[DROP TABLE (Transact-SQL)](../t-sql/statements/drop-table-transact-sql.md)  
[DROP DATABASE (Transact-SQL)](../t-sql/statements/drop-database-transact-sql.md)  
  
  
  

