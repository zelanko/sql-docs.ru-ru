---
title: Удаление объектов базы данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 807dbb9143a02e78b56c6af84fb804a1ae04b92c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34582086"
---
# <a name="lesson-3-1---deleting-database-objects"></a>Урок 3–1. Удаление объектов базы данных
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
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
    DROP VIEW vw_Names;  
    GO  
  
    ```  
  
7.  С помощью инструкции `DELETE` удаляются все строки таблицы `Products` :  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  С помощью инструкции `DROP` удаляется таблица `Products` :  
  
    ```  
    DROP TABLE Products;  
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
  
  
  
