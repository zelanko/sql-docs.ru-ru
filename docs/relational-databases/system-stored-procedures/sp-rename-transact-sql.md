---
title: "sp_rename (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/09/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_rename_TSQL
- sp_rename
dev_langs: TSQL
helpviewer_keywords:
- renaming indexes
- renaming columns
- sp_rename
- renaming tables
ms.assetid: bc3548f0-143f-404e-a2e9-0a15960fc8ed
caps.latest.revision: "54"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 158974d93e031d689318ea22f3bd0ba8189553ee
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="sprename-transact-sql"></a>sp_rename (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет имя пользовательского объекта в текущей базе данных. Этот объект может быть таблицей, индексом, столбцом, псевдонимом типа данных или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] определяемых пользователем типов среды выполнения (CLR).  
  
> [!CAUTION]  
>  Изменение любой части имени объекта может разрушить скрипты и хранимые процедуры. Не рекомендуется использовать эту инструкцию для переименования хранимых процедур, триггеров, определяемых пользователем функций или представлений; следует удалить объект и создать его повторно с новым именем.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rename [ @objname = ] 'object_name' , [ @newname = ] 'new_name'   
    [ , [ @objtype = ] 'object_type' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @objname = ] '*object_name*'  
 Текущее полное или неполное имя пользовательского объекта или типа данных. Если переименовываемый объект представляет собой столбец в таблице, *object_name* должно быть в форме *таблица.столбец* или *столбце schema.table.column*. Если переименовываемый объект представляет собой индекс, *object_name* должно быть в форме *table.index* или *schema.table.index*. Если переименовываемый объект представляет собой ограничение, *object_name* должно быть в форме *schema.constraint*.  
  
 Кавычки необходимы, только если указан объект с полным именем. Если предоставлено полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. *object_name* — **nvarchar(776)**, не имеет значения по умолчанию.  
  
 [ @newname = ] '*new_name*'  
 Новое имя для указанного объекта. *новое_имя* должен быть однокомпонентного имени и должны соответствовать правилам для идентификаторов. *Параметр newname* — **sysname**, не имеет значения по умолчанию.  
  
> [!NOTE]  
>  Имена триггеров не могут начинаться с символов # или ##.  
  
 [ @objtype = ] '*object_type*'  
 Тип переименовываемого объекта. *object_type* — **varchar(13)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|COLUMN|Столбец, который будет переименован.|  
|DATABASE|Пользовательская база данных. Этот тип объекта необходим при переименовании базы данных.|  
|INDEX|Пользовательский индекс. При переименовании индекса со статистикой также автоматически переименовывается эта статистика.|  
|OBJECT|Элемент типа, отслеживаемого в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md). Например, значение OBJECT может быть использовано для переименования объектов с ограничениями (CHECK, FOREIGN KEY, PRIMARY/UNIQUE KEY) пользовательских таблиц и правил.|  
|STATISTICS|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> Статистика создается явно пользователем или неявно с индексом. При переименовании статистики для индекса также автоматически переименовывается этот индекс.|  
|USERDATATYPE|Объект [CLR определяемые пользователем типы](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) добавленные выполнением инструкции [CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md) или [sp_addtype](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md).|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Изменить имя объекта или типа данных можно только в текущей базе данных. Имена большинства системных типов данных и системных объектов изменить нельзя.  
  
 Процедура sp_rename автоматически переименовывает ассоциированный индекс каждый раз при переименовании ограничения PRIMARY KEY или UNIQUE. Если переименованный индекс привязан к ограничению PRIMARY KEY, то ограничение PRIMARY KEY также автоматически переименовывается хранимой процедурой sp_rename.  
  
 Процедура sp_rename может использоваться для переименования первичных и вторичных XML-индексов.  
  
 Переименование хранимой процедуры, функции, представления или триггера не изменит имени соответствующего объекта в определении столбца [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) представления каталога или получить с помощью [OBJECT_ ОПРЕДЕЛЕНИЕ](../../t-sql/functions/object-definition-transact-sql.md) встроенной функции. Поэтому не рекомендуется использовать процедуру sp_rename для переименования объектов этих типов. Лучше удалить и создать объект повторно с новым именем.  
  
 Переименование такого объекта, как таблица или столбец не приводит к автоматическому переименованию ссылок на этот объект. Необходимо вручную изменить любые объекты, которые ссылаются на переименованный объект. Например, если переименован столбец таблицы и на этот столбец имеется ссылка в триггере, то необходимо изменить триггер, указав новое имя столбца. Используйте [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) , чтобы составить список зависимостей для объекта перед его переименованием.  
  
## <a name="permissions"></a>Разрешения  
 Для переименования объектов, столбцов и индексов требуется разрешение ALTER на объект. Для переименования определенных пользователем типов требуется разрешение CONTROL на тип. Для переименования базы данных требуется членство в предопределенных ролях сервера sysadmin или dbcreator.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-renaming-a-table"></a>A. Переименование таблицы  
 В следующем примере столбец `SalesTerritory` в таблице `SalesTerr` переименовывается в `Sales` .  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
GO  
```  
  
### <a name="b-renaming-a-column"></a>Б. Переименование столбца  
 Следующий пример переименовывает `TerritoryID` столбца в `SalesTerritory` таблицу `TerrID`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
GO  
```  
  
### <a name="c-renaming-an-index"></a>В. Переименование индекса  
 В следующем примере индекс `IX_ProductVendor_VendorID` переименовывается в `IX_VendorID`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';  
GO  
```  
  
### <a name="d-renaming-an-alias-data-type"></a>Г. Переименование псевдонима типа данных  
 В следующем примере псевдоним типа данных `Phone` переименовывается в `Telephone`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_rename N'Phone', N'Telephone', N'USERDATATYPE';  
GO  
```  
  
### <a name="e-renaming-constraints"></a>Д. Переименование ограничений  
 Следующие примеры иллюстрируют переименование ограничения PRIMARY KEY, ограничения CHECK и ограничения FOREIGN KEY. При переименовании ограничения должна быть указана схема, к которой принадлежит ограничение.  
  
```  
USE AdventureWorks2012;   
GO  
-- Return the current Primary Key, Foreign Key and Check constraints for the Employee table.  
SELECT name, SCHEMA_NAME(schema_id) AS schema_name, type_desc  
FROM sys.objects  
WHERE parent_object_id = (OBJECT_ID('HumanResources.Employee'))   
AND type IN ('C','F', 'PK');   
GO  
  
-- Rename the primary key constraint.  
sp_rename 'HumanResources.PK_Employee_BusinessEntityID', 'PK_EmployeeID';  
GO  
  
-- Rename a check constraint.  
sp_rename 'HumanResources.CK_Employee_BirthDate', 'CK_BirthDate';  
GO  
  
-- Rename a foreign key constraint.  
sp_rename 'HumanResources.FK_Employee_Person_BusinessEntityID', 'FK_EmployeeID';  
  
-- Return the current Primary Key, Foreign Key and Check constraints for the Employee table.  
SELECT name, SCHEMA_NAME(schema_id) AS schema_name, type_desc  
FROM sys.objects  
WHERE parent_object_id = (OBJECT_ID('HumanResources.Employee'))   
AND type IN ('C','F', 'PK');  
  
```  
  
```  
  
name                                  schema_name        type_desc  
------------------------------------- ------------------ ----------------------  
FK_Employee_Person_BusinessEntityID   HumanResources     FOREIGN_KEY_CONSTRAINT  
PK_Employee_BusinessEntityID          HumanResources     PRIMARY_KEY_CONSTRAINT  
CK_Employee_BirthDate                 HumanResources     CHECK_CONSTRAINT  
CK_Employee_MaritalStatus             HumanResources     CHECK_CONSTRAINT  
CK_Employee_HireDate                  HumanResources     CHECK_CONSTRAINT  
CK_Employee_Gender                    HumanResources     CHECK_CONSTRAINT  
CK_Employee_VacationHours             HumanResources     CHECK_CONSTRAINT  
CK_Employee_SickLeaveHours            HumanResources     CHECK_CONSTRAINT  
  
(7 row(s) affected)  
  
name                                  schema_name        type_desc  
------------------------------------- ------------------ ----------------------  
FK_Employee_ID                        HumanResources     FOREIGN_KEY_CONSTRAINT  
PK_Employee_ID                        HumanResources     PRIMARY_KEY_CONSTRAINT  
CK_BirthDate                          HumanResources     CHECK_CONSTRAINT  
CK_Employee_MaritalStatus             HumanResources     CHECK_CONSTRAINT  
CK_Employee_HireDate                  HumanResources     CHECK_CONSTRAINT  
CK_Employee_Gender                    HumanResources     CHECK_CONSTRAINT  
CK_Employee_VacationHours             HumanResources     CHECK_CONSTRAINT  
CK_Employee_SickLeaveHours            HumanResources     CHECK_CONSTRAINT  
  
(7 row(s) affected)  
  
```  
  
### <a name="f-renaming-statistics"></a>Е. Переименование статистики  
 В следующем примере создается объект статистики, с именем contactMail1 и затем переименовывается в NewContact с помощью хранимой процедуры sp_rename. При переименовании объекта статистики его имя должно быть указано в формате schema.table.statistics_name.  
  
```  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
  
sp_rename 'Person.Person.ContactMail1', 'NewContact','Statistics';  
  
```  
  
## <a name="see-also"></a>См. также  
 [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Компонент Database Engine хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
