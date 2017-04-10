---
title: "Изменение или переименование триггеров DML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-dml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "переименование триггеров"
  - "изменение триггеров"
  - "триггеры DML, изменение"
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Изменение или переименование триггеров DML
  В этом разделе описывается процедура изменения или переименования триггера DML в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Для изменения или переименования триггера DML используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Во время переименования триггер должен находиться в текущей базе данных, а новое имя должно удовлетворять правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Не рекомендуется использовать для переименования триггера хранимую процедуру [sp_rename](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md). Изменение любой части имени объекта может разрушить скрипты и хранимые процедуры. При переименовании триггера не изменяется имя соответствующего объекта в определении столбца представления каталога [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md). Вместо этого рекомендуется удалить триггер и снова создать его.  
  
-   Если изменилось имя объекта, на который ссылается триггер, текст триггера необходимо соответствующим образом изменить. Поэтому перед переименованием объекта вначале отобразите зависимости объекта, чтобы определить, не повлияет ли предлагаемое изменение на работу каких-либо триггеров.  
  
-   Кроме того, триггер DML можно изменить, чтобы зашифровать его определение.  
  
-   Для просмотра зависимостей триггера можно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или следующую функцию и представления каталога:  
  
    -   [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
    -   [Функция динамического управления sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
    -   [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для изменения триггера DML требуется разрешение ALTER в таблице или представлении, в котором определен триггер.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Изменение триггера DML  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните нужную базу данных, разверните узел **Таблицы**, а затем разверните таблицу, которая содержит изменяемый триггер.  
  
3.  Разверните узел **Триггеры**, щелкните правой кнопкой мыши изменяемый триггер и выберите команду **Изменить**.  
  
4.  Измените триггер и нажмите кнопку **Выполнить**.  
  
#### Переименование триггера DML  
  
1.  [Удалите триггер](../../relational-databases/triggers/delete-or-disable-dml-triggers.md) , который нужно переименовать.  
  
2.  [Повторно создайте триггер](../../relational-databases/triggers/create-dml-triggers.md), указав новое имя.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Изменение триггера с помощью ALTER TRIGGER  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующие примеры в запрос. Выполните первый пример, чтобы создать триггер DML, который выводит на клиент определяемое пользователем сообщение, когда пользователь пытается добавить или изменить данные в таблице `SalesPersonQuotaHistory`. Выполните инструкцию [ALTER TRIGGER](../../t-sql/statements/alter-trigger-transact-sql.md) , чтобы изменить триггер так, чтобы он срабатывал только на операции `INSERT` . Этот триггер полезен, так как он напоминает пользователям, что при обновлениях и вставках строк в эту таблицу необходимо направить уведомление в отдел `Compensation` .  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### Переименование триггера с помощью инструкций DROP TRIGGER и ALTER TRIGGER  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере инструкции [DROP TRIGGER](../../t-sql/statements/drop-trigger-transact-sql.md) и [ALTER TRIGGER](../../t-sql/statements/alter-trigger-transact-sql.md) используются для переименования триггера `Sales.bonus_reminder` в `Sales.bonus_reminder_2`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## См. также:  
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER (Transact-SQL)](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER (Transact-SQL)](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Получение сведений о триггерах DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  