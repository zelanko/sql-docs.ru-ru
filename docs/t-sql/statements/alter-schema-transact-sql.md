---
title: "Разрешение ALTER SCHEMA (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SCHEMA
- ALTER_SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], transferring
- transferring objects between schemas
- ALTER SCHEMA statement
- schemas [SQL Server], modifying
- modifying schemas
ms.assetid: 0a760138-460e-410a-a3c1-d60af03bf2ed
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad157c7d4d7b92bc199c4a490d4387acc0af0908
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

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
  
 \<entity_type >  
 Класс сущности, для которой изменяется владелец. По умолчанию это объект.  
  
 *securable_name*  
 Одно- или двухкомпонентное имя содержащейся в схеме защищаемой сущности, которая должна быть перемещена в другую схему.  
  
## <a name="remarks"></a>Замечания  
 Пользователи и схемы полностью разделены.  
  
 Инструкция ALTER SCHEMA применяется только для перемещения защищаемых объектов между схемами в пределах одной базы данных. Для изменения или удаления защищаемой сущности в схеме используйте инструкцию ALTER или DROP, специфичную для этой сущности.  
  
 При использовании однокомпонентного имени *securable_name*, правила разрешения имен действующих будет использоваться для поиска защищаемой.  
  
 Все разрешения, связанные с защищаемой сущностью, при перемещении в другую схему будут удалены. Если владелец защищаемой сущности был явно указан, он не изменится. Если для владельца защищаемой схемы было установлено значение SCHEMA OWNER, то владельцем останется SCHEMA OWNER. Однако после перемещения SCHEMA OWNER будет относиться к владельцу новой схемы. Значение principal_id нового владельца будет равно NULL.  
  
 Чтобы изменить схему таблицы или представления с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], в обозревателе объектов щелкните правой кнопкой мыши таблицу или представление и нажмите кнопку **конструктора**. Нажмите клавишу **F4** для открытия окна «Свойства». В **схемы** выберите новую схему.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Для передачи защищаемой сущности из другой схемы текущий пользователь должен иметь разрешения CONTROL на эту сущность (а не на схему) и разрешения ALTER на целевую схему.  
  
 Если защищаемая сущность имеет спецификацию EXECUTE AS OWNER, а ее владельцем является SCHEMA OWNER, у пользователя также должно быть разрешение IMPERSONATION на владельца целевой схемы.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Создание СХЕМЫ &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [Удаление СХЕМЫ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


