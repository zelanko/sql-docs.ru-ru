---
title: Удаление объектов базы данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 555c51cca7b853a39831eebbd736794b0f0ffd69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095137"
---
# <a name="deleting-database-objects"></a>Удаление объектов базы данных
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
 [Учебник. Составление инструкций Transact-SQL](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>См. также  
 [REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql)   
 [DROP USER (Transact-SQL)](/sql/t-sql/statements/drop-user-transact-sql)   
 [DROP LOGIN (Transact-SQL)](/sql/t-sql/statements/drop-login-transact-sql)   
 [DROP PROCEDURE (Transact-SQL)](/sql/t-sql/statements/drop-procedure-transact-sql)   
 [DROP VIEW (Transact-SQL)](/sql/t-sql/statements/drop-view-transact-sql)   
 [DELETE (Transact-SQL)](/sql/t-sql/statements/delete-transact-sql)   
 [DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql)   
 [DROP DATABASE (Transact-SQL)](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
