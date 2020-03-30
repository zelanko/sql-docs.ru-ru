---
title: Просмотр определения хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: de250fd158bdd02764e992e0ccbb69e072b4c6ab
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72907337"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>Просмотр определения хранимой процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
    
##  <a name="you-can-view-the-definition-of-a-stored-procedure-in-ssmanstudiofull-using-object-explorer-menu-options-or-in-the-query-editor-using-tsql-this-topic-describes-how-to-view-the-definition-of-procedure-in-object-explorer-and-by-using-a-system-stored-procedure-system-function-and-object-catalog-view-in-the-query-editor"></a><a name="Top"></a> Определение хранимой процедуры можно просмотреть в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , воспользовавшись параметрами меню обозревателя объектов, а также с помощью редактора запросов и языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. В данном разделе описывается процесс просмотра определения хранимой процедуры в обозревателе объектов и с помощью хранимой в системе процедуры, системной функции и в представлении каталога объектов в редакторе запросов.  
  
-   **Перед началом работы**  [Безопасность](#Security)  
  
-   **Просмотр определения хранимой процедуры с помощью**  [среды SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Системная хранимая процедура: **sp_helptext**  
 Необходимо быть членом роли **public**. Определения системных объектов видимы для всех. Определения пользовательских объектов видимы владельцу объекта или получателям, которым предоставлено одно из следующих разрешений: ALTER, CONTROL, TAKE OWNERSHIP или VIEW DEFINITION.  
  
 Системная функция: **OBJECT_DEFINITION**  
 Определения системных объектов видимы для всех. Определения пользовательских объектов видимы владельцу объекта или получателям, которым предоставлено одно из следующих разрешений: ALTER, CONTROL, TAKE OWNERSHIP или VIEW DEFINITION. Эти разрешения неявно предоставляются членам предопределенных ролей базы данных **db_owner**, **db_ddladmin**и **db_securityadmin** .  
  
 Представление каталога объектов: **sys.sql_modules**  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> Просмотр определения хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр определения процедуры средствами обозревателя объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните пункт **Хранимые процедуры**, щелкните правой кнопкой процедуру, после чего щелкните пункт **Создать скрипт для хранимой процедуры как**, после чего щелкните один из следующих пунктов: **Создать в**, **Изменить на** или **Удалить и создать в**.  
  
4.  Выберите **New Query Editor Window** (Окно редактирования нового запроса). При этом отобразится определение процедуры.  

###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр определения процедуры в редакторе запросов**  
  
 Системная хранимая процедура: **sp_helptext**  
 1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующую инструкцию, которая использует системную хранимую процедуру **sp_helptext** . Измените имя базы данных и имя хранимой процедуры для ссылки на нужную базу данных и хранимую процедуру.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 Системная функция: **OBJECT_DEFINITION**  
 1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующие инструкции, которые используют системную функцию **OBJECT_DEFINITION** . Измените имя базы данных и имя хранимой процедуры для ссылки на нужную базу данных и хранимую процедуру.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Представление каталога объектов: **sys.sql_modules**  
 1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
3.  В окне запроса введите следующие инструкции, которые используют представление каталогов **sys.sql_modules** . Измените имя базы данных и имя хранимой процедуры для ссылки на нужную базу данных и хранимую процедуру.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Создание хранимой процедуры](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Изменение хранимой процедуры](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Удаление хранимой процедуры](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)   
 [Изменение имени хранимой процедуры](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION (Transact-SQL)](../../t-sql/functions/object-definition-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [OBJECT_ID (Transact-SQL)](../../t-sql/functions/object-id-transact-sql.md)  
  
  
