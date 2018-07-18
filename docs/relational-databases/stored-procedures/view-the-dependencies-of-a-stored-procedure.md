---
title: Просмотр зависимостей хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c85d42da5d49d9d3836a029f6e191cec9a24c2f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332674"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a>Просмотр зависимостей хранимой процедуры
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В этом разделе описывается, как просмотреть зависимости хранимой процедуры [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
##  <a name="Top"></a>   
-   **Перед началом:**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Системная функция: **sys.dm_sql_referencing_entities**  
 Необходимо разрешение CONTROL на упоминаемую сущность и разрешение SELECT на представление sys.dm_sql_referencing_entities. Если упоминаемая сущность является функцией секционирования, необходимо разрешение CONTROL на базу данных. Разрешение SELECT по умолчанию предоставляется роли public.  
  
 Системная функция: **sys.dm_sql_referenced_entities**  
 Требует разрешения SELECT для функции sys.dm_sql_referenced_entities и разрешения VIEW DEFINITION для ссылающейся сущности. Разрешение SELECT по умолчанию предоставляется роли public. Требует разрешения VIEW DEFINITION для базы данных, либо, если ссылающаяся сущность является триггером DDL уровня базы данных, разрешения ALTER DATABASE DDL TRIGGER. Если указанный модуль является триггером DDL уровня сервера, то требуется разрешение VIEW ANY DEFINITION на уровне сервера.  
  
 Представление каталога объектов: **sys.sql_expression_dependencies**  
 Необходимо разрешение VIEW DEFINITION в базе данных и разрешение SELECT на представление sys.sql_expression_dependencies в базе данных. По умолчанию разрешение SELECT предоставляется только членам предопределенной роли базы данных db_owner. Если разрешения SELECT и VIEW DEFINITION предоставлены другому пользователю, он может просматривать все зависимости в базе данных.  
  
##  <a name="Procedures"></a> Просмотр зависимостей хранимой процедуры  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр зависимостей процедуры в обозревателе объектов**  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните узел **Хранимые процедуры**, щелкните процедуру правой кнопкой мыши и выберите пункт **Просмотреть зависимости**.  
  
4.  Просмотрите список объектов, находящихся в зависимости от процедуры.  
  
5.  Просмотрите список объектов, от которых зависит данная процедура.  
  
6.  Нажмите кнопку **ОК**.  
  
###  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр зависимостей процедуры в редакторе запросов**  
  
 Системная функция: **sys.dm_sql_referencing_entities**  
 Эта функция используется для отображения объектов, зависящих от процедуры.  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  После того как процедура будет создана, во втором примере будет использована функция sys.dm_sql_referencing_entities для отображения объектов, зависящих от процедуры.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 Системная функция: **sys.dm_sql_referenced_entities**  
 Эта функция используется для отображения объектов, от которых зависит процедура.  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  После того как процедура будет создана, во втором примере будет использована функция sys.dm_sql_referencing_entities для отображения объектов, зависящих от процедуры.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 Представление каталога объектов: **sys.sql_expression_dependencies**  
 Это представление можно использовать для отображения объектов, от которых зависит процедура или которые зависят от процедуры.  
  
 Отображение объектов зависит от процедуры.  
 1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  После того как процедура будет создана, во втором примере будет использовано представление sys.sql_expression_dependencies для отображения объектов, зависящих от процедуры.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 Отображение объектов, от которых зависит процедура.  
 1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных, в которой находится процедура.  
  
3.  Выберите команду **Создать запрос** в меню **Файл** .  
  
4.  Скопируйте и вставьте следующие примеры в редактор запросов. В первом примере будет создана процедура `uspVendorAllInfo` , которая возвращает для всех поставщиков в базе данных [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] их имена, поставляемую продукцию, кредитные рейтинги и доступность.  
  
    ```  
    USE AdventureWorks2008R2;  
    GO  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
    ```  
  
5.  После того как процедура будет создана, во втором примере будет использовано представление sys.sql_expression_dependencies для отображения объектов, от которых зависит процедура.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo');  
    GO  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Изменение имени хранимой процедуры](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
  
