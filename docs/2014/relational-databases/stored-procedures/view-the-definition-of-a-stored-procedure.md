---
title: Просмотр определения хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 333d4d9f0ab9feb5d5b5c4d0aa48fd584cef3143
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856513"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>Просмотр определения хранимой процедуры
    
##  <a name="Top"></a> Определение хранимой процедуры можно просмотреть в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , воспользовавшись параметрами меню обозревателя объектов, а также с помощью редактора запросов и языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. В данном разделе описывается процесс просмотра определения хранимой процедуры в обозревателе объектов и с помощью хранимой в системе процедуры, системной функции и в представлении каталога объектов в редакторе запросов.  
  
-   **Перед началом:**  [Безопасность](#Security)  
  
-   **Просмотр определения хранимой процедуры с помощью:**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Системная хранимая процедура: `sp_helptext`  
 Необходимо быть членом роли **public**. Определения системных объектов видимы для всех. Определения пользовательских объектов является видимым для владельца объекта или участникам, которым предоставлены следующие разрешения: ALTER, элемент УПРАВЛЕНИЯ, TAKE OWNERSHIP или VIEW DEFINITION.  
  
 Системная функция: `OBJECT_DEFINITION`  
 Определения системных объектов видимы для всех. Определения пользовательских объектов является видимым для владельца объекта или участникам, которым предоставлены следующие разрешения: ALTER, элемент УПРАВЛЕНИЯ, TAKE OWNERSHIP или VIEW DEFINITION. Эти разрешения неявно предоставляются членам предопределенных ролей базы данных **db_owner**, **db_ddladmin**и **db_securityadmin** .  
  
 Представление каталога объектов: `sys.sql_modules`  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).  
  
##  <a name="Procedures"></a> Просмотр определения хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр определения процедуры средствами обозревателя объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните **хранимые процедуры**, щелкните процедуру правой кнопкой мыши и выберите команду **скрипт для хранимой процедуры**, а затем выберите один из следующих: **Чтобы создать**, **Alter для**, или **удалить и создать в**.  
  
4.  Выберите **Создать окно редактора запросов**. При этом отобразится определение процедуры.  
  
###  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр определения процедуры в редакторе запросов**  
  
 Системная хранимая процедура: `sp_helptext`  
 1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующую инструкцию, которая использует системную хранимую процедуру `sp_helptext`. Измените имя базы данных и имя хранимой процедуры для ссылки на нужную базу данных и хранимую процедуру.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 Системная функция: `OBJECT_DEFINITION`  
 1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующие инструкции, которые используют системную функцию `OBJECT_DEFINITION`. Измените имя базы данных и имя хранимой процедуры для ссылки на нужную базу данных и хранимую процедуру.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Представление каталога объектов: `sys.sql_modules`  
 1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующие инструкции, которые используют представление каталогов `sys.sql_modules`. Измените имя базы данных и имя хранимой процедуры для ссылки на нужную базу данных и хранимую процедуру.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>См. также  
 [Создание хранимой процедуры](create-a-stored-procedure.md)   
 [Изменение хранимой процедуры](modify-a-stored-procedure.md)   
 [Удаление хранимой процедуры](delete-a-stored-procedure.md)   
 [Изменение имени хранимой процедуры](rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION (Transact-SQL)](/sql/t-sql/functions/object-definition-transact-sql)   
 [sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sp_helptext (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)   
 [OBJECT_ID (Transact-SQL)](/sql/t-sql/functions/object-id-transact-sql)  
  
  
