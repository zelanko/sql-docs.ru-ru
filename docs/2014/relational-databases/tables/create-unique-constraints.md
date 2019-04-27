---
title: Создание ограничения уникальности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77581cc6d8838e0cfed4bb7cc615f4d1f58de0d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761461"
---
# <a name="create-unique-constraints"></a>Создание ограничений уникальности
  Можно создать ограничение уникальности в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] , чтобы гарантировать, что в определенных столбцах, не участвующих в первичном ключе, не будут встречаться повторяющиеся значения. Создание ограничения уникальности автоматически приводит к созданию соответствующего уникального индекса.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Создание ограничения уникальности с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-unique-constraint"></a>Создание ограничения уникальности  
  
1.  В **Обозревателе объектов**щелкните правой кнопкой мыши таблицу, в которую необходимо добавить ограничение уникальности, и выберите **Конструктор**.  
  
2.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
3.  В диалоговом окне **Индексы и ключи** нажмите **Добавить**.  
  
4.  В сетке в разделе **Общие**щелкните **Тип** и выберите **Уникальный ключ** в раскрывающемся списке справа от свойства.  
  
5.  В меню **Файл** выберите пункт **Сохранить**_table name_.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-unique-constraint"></a>Создание ограничения уникальности  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создаются таблица `TransactionHistoryArchive4` и ограничение уникальности в столбце `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a>Создание ограничения уникальности в существующей таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается ограничение уникальности в столбцах `PasswordHash` и `PasswordSalt` в таблице `Person.Password`.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a>Создание ограничения уникальности в новой таблице  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается таблица и определяется ограничение уникальности в столбце `TransactionID`.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     Дополнительные сведения см. в статьях [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) и [table_constraint (Transact-SQL)](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).  
  
###  <a name="TsqlExample"></a>  
