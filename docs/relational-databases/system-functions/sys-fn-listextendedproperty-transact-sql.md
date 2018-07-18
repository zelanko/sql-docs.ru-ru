---
title: sys.fn_listextendedproperty (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_listextendedproperty
- fn_listextendedproperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_listextendedproperty function
- displaying extended properties
- database extended properties [SQL Server]
- viewing extended properties
- column extended properties [SQL Server]
- sys.fn_listextendedproperties function
- database objects [SQL Server], extended properties
- extended properties [SQL Server], columns
- table extended properties [SQL Server]
ms.assetid: 59bbb91f-a277-4a35-803e-dcb91e847a49
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3484c32c00c5f94f084cd5c0e49837181054df40
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238441"
---
# <a name="sysfnlistextendedproperty-transact-sql"></a>sys.fn_listextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает значения расширенных свойств объектов базы данных.  
 
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_listextendedproperty (   
    { default | 'property_name' | NULL }   
  , { default | 'level0_object_type' | NULL }   
  , { default | 'level0_object_name' | NULL }   
  , { default | 'level1_object_type' | NULL }   
  , { default | 'level1_object_name' | NULL }   
  , { default | 'level2_object_type' | NULL }   
  , { default | 'level2_object_name' | NULL }   
  )   
```  
  
## <a name="arguments"></a>Аргументы  
 {по умолчанию | "*property_name*" | NULL}  
 Имя свойства. *property_name* — **sysname**. Допустимыми входными значениями являются default, NULL или имя свойства.  
  
 {по умолчанию | "*level0_object_type*" | NULL}  
 Пользователь или тип, определяемый пользователем. *level0_object_type* — **varchar(128)**, значение по умолчанию NULL. Допустимые входные значения: ASSEMBLY, CONTRACT, EVENT NOTIFICATION, FILEGROUP, MESSAGE TYPE, PARTITION FUNCTION, PARTITION SCHEME, REMOTE SERVICE BINDING, ROUTE, SCHEMA, SERVICE, TRIGGER, TYPE, USER и значение NULL.  
  
> [!IMPORTANT]  
>  Типы USER и TYPE уровня 0 будут удалены в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время. Тип SCHEMA следует использовать в качестве типа уровня 0 вместо USER. В значении аргумента TYPE следует указывать тип SCHEMA в качестве типа уровня 0 и TYPE в качестве типа уровня 1.  
  
 {по умолчанию | "*level0_object_name*" | NULL}  
 Имя указанного типа объекта уровня 0. *level0_object_name* — **sysname** значение по умолчанию NULL. Допустимыми входными значениями являются значение по умолчанию, NULL или имя объекта.  
  
 {по умолчанию | "*level1_object_type*" | NULL}  
 Тип объекта уровня 1. *level1_object_type* — **varchar(128)** значение по умолчанию NULL. Допустимые входные значения: AGGREGATE, DEFAULT, FUNCTION, LOGICAL FILE NAME, PROCEDURE, QUEUE, RULE, SYNONYM, TABLE, TYPE, VIEW, XML SCHEMA COLLECTION и NULL.  
  
> [!NOTE]  
>  Значение по умолчанию сопоставлено значению NULL, и значение «default» сопоставлено типу объектов DEFAULT.  
  
 {по умолчанию | "*level1_object_name*" | NULL}  
 Имя указанного типа объекта уровня 1. *level1_object_name* — **sysname** значение по умолчанию NULL. Допустимыми входными значениями являются значение по умолчанию, NULL или имя объекта.  
  
 {по умолчанию | "*level2_object_type*" | NULL}  
 Тип объекта уровня 2. *level2_object_type* — **varchar(128)** значение по умолчанию NULL. Допустимыми входными значениями являются DEFAULT, значение по умолчанию (сопоставленное значению NULL) и значение NULL. Допустимые входные данные для *level2_object_type* СТОЛБЦА, ограничения, уведомления о СОБЫТИИ, ИНДЕКСА, параметр, триггер и NULL.  
  
 {по умолчанию | "*level2_object_name*" | NULL}  
 Имя указанного типа объекта уровня 2. *level2_object_name* — **sysname** значение по умолчанию NULL. Допустимыми входными значениями являются значение по умолчанию, NULL или имя объекта.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Это формат таблиц, возвращаемых функцией fn_listextendedproperty.  
  
|Имя столбца|Тип данных|  
|-----------------|---------------|  
|objtype|**sysname**|  
|objname|**sysname**|  
|имя|**sysname**|  
|value|**sql_variant**|  
  
 Возвращение пустой таблицы означает отсутствие у объекта расширенных свойств или отсутствие у пользователя разрешений на просмотр этих свойств. При возвращении расширенных свойств самой базы данных столбцы objtype и objname принимают значения NULL.  
  
## <a name="remarks"></a>Замечания  
 Если значение для *property_name* имеет значение NULL или по умолчанию, функция fn_listextendedproperty возвращает все свойства для указанного объекта.  
  
 Если указан тип объекта, а значение, соответствующее имени объекта, равно NULL или значению по умолчанию, функция fn_listextendedproperty возвращает все расширенные свойства всех объектов заданного типа.  
  
 Объекты различаются по уровню: нулевой уровень является наивысшим, а второй — низшим. Если для объекта низкого уровня (1 или 2) указаны тип и имя, то для родительского объекта значения типа и имени не могут иметь значение NULL или значение по умолчанию. В противном случае функция возвращает пустой результирующий набор.  
  
 **ObjName** зафиксировано как Latin1_General_CI_AI. Однако вы можете решение это путем переопределения параметров сортировки для сравнения.  
  
```  
SELECT o.[object_id] AS 'table_id', o.[name] 'table_name',  
0 AS 'column_order', NULL AS 'column_name', NULL AS 'column_datatype',  
NULL AS 'column_length', Cast(e.value AS varchar(500)) AS 'column_description'  
FROM AdventureWorks.sys.objects AS o  
LEFT JOIN sys.fn_listextendedproperty(N'MS_Description', N'user',N'HumanResources',N'table', N'Employee', null, default) AS e  
    ON o.name = e.objname COLLATE SQL_Latin1_General_CP1_CI_AS  
WHERE o.name = 'Employee';  
```  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на просмотр расширенных свойств объектов зависят от типов объектов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. Отображение расширенных свойств базы данных  
 В следующем примере выводится полный набор расширенных свойств объекта базы данных.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty(default, default, default, default, default, default, default);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `objtype    objname     name            value`  
  
 `---------  ---------   -----------     ----------------------------`  
  
 `NULL       NULL        MS_Description  AdventureWorks2008 Sample OLTP Database`  
  
 `(1 row(s) affected)`  
  
### <a name="b-displaying-extended-properties-on-all-columns-in-a-table"></a>Б. Отображение расширенных свойств для всех столбцов таблицы  
 В следующем примере выводится список расширенных свойств для столбцов в `ScrapReason` таблицы. Она хранится в схеме `Production`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty (NULL, 'schema', 'Production', 'table', 'ScrapReason', 'column', default);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `objtype objname      name            value`  
  
 `------- -----------  -------------   ------------------------`  
  
 `COLUMN ScrapReasonID MS_Description  Primary key for ScrapReason records.`  
  
 `COLUMN Name          MS_Description  Failure description.`  
  
 `COLUMN ModifiedDate  MS_Description  Date the record was last updated.`  
  
 `(3 row(s) affected)`  
  
### <a name="c-displaying-extended-properties-on-all-tables-in-a-schema"></a>В. Отображение расширенных свойств для всех таблиц схемы  
 В следующем примере выводится список расширенных свойств для всех таблиц, содержащихся в `Sales` схемы.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty (NULL, 'schema', 'Sales', 'table', default, NULL, NULL);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
