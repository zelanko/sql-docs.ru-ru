---
title: "Разрешение ALTER SCHEMA (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/09/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SCHEMA
- ALTER_SCHEMA_TSQL
dev_langs: TSQL
helpviewer_keywords:
- objects [SQL Server], transferring
- transferring objects between schemas
- ALTER SCHEMA statement
- schemas [SQL Server], modifying
- modifying schemas
ms.assetid: 0a760138-460e-410a-a3c1-d60af03bf2ed
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 30ef553ccfba1f30be9b75f8d0290115be395925
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="alter-schema-transact-sql"></a>ALTER SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Передача защищаемых сущностей между схемами.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER SCHEMA schema_name   
   TRANSFER [ <entity_type> :: ] securable_name   
[;]  
  
<entity_type> ::=  
    {  
    Object | Type | XML Schema Collection  
    }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER SCHEMA schema_name   
   TRANSFER [ OBJECT :: ] securable_name   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы в текущей базе данных, в которую будет перемещена защищаемая сущность. Не может иметь значение SYS или INFORMATION_SCHEMA.  
  
 \<entity_type>  
 Класс сущности, для которой изменяется владелец. По умолчанию это объект.  
  
 *securable_name*  
 Одно- или двухкомпонентное имя схемы является защищаемой сущности, перемещена в другую схему.  
  
## <a name="remarks"></a>Remarks  
 Пользователи и схемы полностью разделены.  
  
 Инструкция ALTER SCHEMA применяется только для перемещения защищаемых объектов между схемами в пределах одной базы данных. Для изменения или удаления защищаемой сущности в схеме используйте инструкцию ALTER или DROP, специфичную для этой сущности.  
  
 При использовании однокомпонентного имени *securable_name*, правила разрешения имен действующих будет использоваться для поиска защищаемой.  
  
 Все разрешения, связанные с защищаемой сущностью, при перемещении в другую схему будут удалены. Если владелец защищаемой сущности был явно указан, он не изменится. Если для владельца защищаемой схемы было установлено значение SCHEMA OWNER, то владельцем останется SCHEMA OWNER. Однако после перемещения SCHEMA OWNER будет относиться к владельцу новой схемы. Значение principal_id нового владельца будет равно NULL.  
  
 Перемещение хранимой процедуры, функции, представления или триггера не изменит имя схемы, если присутствует соответствующего объекта в определении столбца [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) представления каталога или получить с помощью [ OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) встроенной функции. Таким образом рекомендуется не использовать ALTER SCHEMA для перемещения объектов этих типов. Вместо этого удалите и повторно создать объект в его новой схемы.  
  
 Перемещение объекта, например таблицы или синоним не будут автоматически обновляться ссылки на этот объект. Необходимо изменить все объекты, которые ссылаются на переносятся объект вручную. Например если переместить таблицу и эту таблицу имеется ссылка в триггере, необходимо изменить триггер, указав новое имя схемы. Используйте [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) Чтобы составить список зависимостей для объекта перед его перемещением.  

 Чтобы изменить схему таблицы с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], в обозревателе объектов щелкните правой кнопкой мыши в таблице и нажмите кнопку **конструктора**. Нажмите клавишу **F4** для открытия окна «Свойства». В **схемы** выберите новую схему.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Разрешения  
 Для передачи защищаемой сущности из другой схемы текущий пользователь должен иметь разрешения CONTROL на эту сущность (а не на схему) и разрешения ALTER на целевую схему.  
  
 Если Защищаемая сущность имеет спецификацию EXECUTE AS OWNER на нем и владельца, установлено значение SCHEMA OWNER, пользователь должен также иметь разрешение IMPERSONATE для владельца целевой схемы.  
  
 Все разрешения, связанные с перемещаемой защищаемой сущностью, при перемещении удаляются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-transferring-ownership-of-a-table"></a>A. Передача владения таблицей  
 В следующем примере схема `HumanResources` изменяется путем перемещения в нее таблицы `Address` из схемы `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER SCHEMA HumanResources TRANSFER Person.Address;  
GO  
```  
  
### <a name="b-transferring-ownership-of-a-type"></a>Б. Передача владения типом  
 В следующем примере создается тип в схеме `Production`, а затем этот тип передается схеме `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TYPE Production.TestType FROM [varchar](10) NOT NULL ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
  
-- Change the type to the Person schema.  
ALTER SCHEMA Person TRANSFER type::Production.TestType ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-transferring-ownership-of-a-table"></a>В. Передача владения таблицей  
 Следующий пример создает таблицу `Region` в `dbo` создает схему, `Sales` схему, а затем переходит `Region` таблицу `dbo` схемы для `Sales` схемы.  
  
```  
CREATE TABLE dbo.Region   
    (Region_id int NOT NULL,  
    Region_Name char(5) NOT NULL)  
WITH (DISTRIBUTION = REPLICATE);  
GO  
  
CREATE SCHEMA Sales;  
GO  
  
ALTER SCHEMA Sales TRANSFER OBJECT::dbo.Region;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Создание СХЕМЫ &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [Удаление СХЕМЫ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

