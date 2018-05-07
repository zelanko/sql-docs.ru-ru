---
title: sys.sql_modules (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: af128c6c3b28c448111f49adf55c66c12ab4bbae
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syssqlmodules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждого объекта, являющегося в модулем, определенным на языке SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая изначально скомпилированные скалярной определяемой пользователем функции. Объекты типа P, RF, V, TR, FN, IF, TF и R имеют сопоставленный с ними SQL модуль. Изолированные значения по умолчанию и объекты типа D в этом представлении также имеют определение SQL модуля. Описание этих типов см. в разделе **тип** столбца в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления каталога.  
  
 Дополнительные сведения см. в разделе [Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, содержащего данный объект. Уникален в базе данных.|  
|**Определение**|**nvarchar(max)**|Текст на языке SQL, определяющий этот модуль. Это значение можно получить с помощью [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) встроенной функции.<br /><br /> NULL = зашифрован.|  
|**uses_ansi_nulls**|**бит**|Модуль был создан с параметром SET ANSI_NULLS ON.<br /><br /> Всегда будет равен 0 (нулю) для правил и умолчаний.|  
|**uses_quoted_identifier**|**бит**|Модуль был создан с параметром SET QUOTED_IDENTIFIER ON.|  
|**is_schema_bound**|**бит**|Модуль был создан с параметром SCHEMABINDING.<br /><br /> Всегда содержит значение 1 для скомпилированных собственными средствами хранимых процедур.|  
|**uses_database_collation**|**бит**|1 = определение модуля, ограниченное схемой, зависит от принятых по умолчанию параметров сортировки базы данных для правильной оценки; в противном случае — 0. Такая зависимость предотвращает изменение параметров сортировки по умолчанию для базы данных.|  
|**is_recompiled**|**бит**|Процедура была создана с параметром WITH RECOMPILE.|  
|**null_on_null_input**|**бит**|Модуль был объявлен, чтобы обеспечить выходные значения NULL для любых входных значений NULL.|  
|**execute_as_principal_id**|**Int**|ID-идентификатор участника базы данных, указанного в инструкции EXECUTE AS.<br /><br /> По умолчанию и в случае EXECUTE AS CALLER имеет значение NULL.<br /><br /> Идентификатор заданного участника, если EXECUTE AS SELF или EXECUTE AS \<основной >.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|**бит**|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].<br /><br /> 0 = не скомпилированы в собственном коде<br /><br /> 1 = скомпилированы в собственном коде<br /><br /> Значение по умолчанию — 0.|  
  
## <a name="remarks"></a>Замечания  
 Выражение SQL для ограничения по умолчанию объект типа D, находится в [sys.default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md) представления каталога. Выражение SQL для ПРОВЕРОЧНОГО ограничения, объектом типа C, находится в [sys.check_constraints](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md) представления каталога.  
  
 Эти сведения также описан в [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 В ходе выполнения представленного ниже примера выполняется отображение имен, типов и определений всех модулей в текущей базе данных.  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
