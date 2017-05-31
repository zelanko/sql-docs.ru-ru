---
title: "Удаление или отключение триггеров DML | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-dml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0fe807c194c057f2109bb40b13a8f8918c0cc75f
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="delete-or-disable-dml-triggers"></a>Удаление или отключение триггеров DML
  В этом разделе описывается удаление или отключение триггера DML в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Для удаления или отключения триггера DML используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   После удаления триггер удаляется из текущей базы данных. Это не повлияет на таблицу и данные, на которых он основан. При удалении таблицы автоматически удаляются все триггеры в ней.  
  
-   По умолчанию при создании триггер включается.  
  
-   Отключение триггера не сбрасывает его. Триггер все еще существует как объект в текущей базе данных. Впрочем, триггер в инструкциях INSERT, UPDATE или DELETE не сработает при выполнении любой из них. Отключенные триггеры можно повторно включать. При включении триггера он не создается повторно. Он срабатывает так же, как после создания.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Чтобы удалить триггер DML, необходимо разрешение ALTER для таблицы или представления, в которых определен данный триггер.  
  
 Для отключения или включения триггера DML пользователь должен обладать как минимум разрешением ALTER для таблицы или представления, где создан триггер.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-dml-trigger"></a>Удаление триггера DML  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните нужную базу данных, разверните узел **Таблицы**, а затем разверните таблицу, которая содержит удаляемый триггер.  
  
3.  Разверните узел **Триггеры**, щелкните правой кнопкой мыши нужный триггер и выберите команду **Удалить**.  
  
4.  В диалоговом окне **Удаление объекта** проверьте триггер и нажмите кнопку **ОК**.  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>Отключение и включение триггера DML  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните нужную базу данных, разверните узел **Таблицы**, а затем разверните таблицу, которая содержит отключаемый триггер.  
  
3.  Разверните узел **Триггеры**, щелкните правой кнопкой мыши нужный триггер и выберите команду **Отключить**.  
  
4.  Чтобы включить триггер, выберите команду **Включить**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-dml-trigger"></a>Удаление триггера DML  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующие примеры в окно запроса. Выполните инструкцию [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) , чтобы создать триггер `Sales.bonus_reminder` . Чтобы удалить триггер, выполните инструкцию [DROP TRIGGER](../../t-sql/statements/drop-trigger-transact-sql.md) .  
  
```tsql  
--Create the trigger.  
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
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>Отключение и включение триггера DML  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте и вставьте следующие примеры в окно запроса. Выполните инструкцию [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md) , чтобы создать триггер `Sales.bonus_reminder` . Чтобы отключить или включить триггер, выполните соответственно инструкцию [DISABLE TRIGGER](../../t-sql/statements/disable-trigger-transact-sql.md) или [ENABLE TRIGGER](../../t-sql/statements/enable-trigger-transact-sql.md) .  
  
```tsql  
--Create the trigger.  
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
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```tsql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER (Transact-SQL)](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER (Transact-SQL)](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
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
  
  
