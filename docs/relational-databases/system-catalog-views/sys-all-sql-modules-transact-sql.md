---
title: sys.all_sql_modules (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- all_sql_modules_TSQL
- sys.all_sql_modules
- all_sql_modules
- sys.all_sql_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_sql_modules catalog view
ms.assetid: 7477a3fe-afb3-44c8-bb2c-c6e1d9bdee6f
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 89a4bc095598a43be8c5261ee263582d156353c5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysallsqlmodules-transact-sql"></a>sys.all_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает объединение **sys.sql_modules** и **sys.system_sql_modules**.  
  
 Представление возвращает по строке для каждого скомпилированных в собственном коде скалярной определяемой пользователем функции. Дополнительные сведения см. в разделе [Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, содержащего данный объект. Уникален в базе данных.|  
|**Определение**|**nvarchar(max)**|Текст на языке SQL, определяющий этот модуль.<br /><br /> NULL = зашифрован|  
|**uses_ansi_nulls**|**бит**|Модуль был создан с параметром SET ANSI_NULLS ON.|  
|**uses_quoted_identifier**|**бит**|Модуль был создан с параметром SET QUOTED_IDENTIFIER ON.|  
|**is_schema_bound**|**бит**|Модуль был создан с параметром SCHEMABINDING.|  
|**uses_database_collation**|**бит**|1 = определение модуля, ограниченное схемой, зависит от принятых по умолчанию параметров сортировки базы данных для правильной оценки; в противном случае — 0. Такая зависимость предотвращает изменение параметров сортировки по умолчанию для базы данных.|  
|**is_recompiled**|**бит**|Процедура была создана с параметром WITH RECOMPILE.|  
|**null_on_null_input**|**бит**|Модуль был объявлен, чтобы обеспечить выходные значения NULL для любых входных значений NULL.|  
|**execute_as_principal_id**|**int**|ID-идентификатор участника базы данных, указанного в инструкции EXECUTE AS.<br /><br /> По умолчанию и в случае EXECUTE AS CALLER имеет значение NULL.<br /><br /> Идентификатор заданного участника, если EXECUTE AS SELF или EXECUTE AS \<основной >.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|bit|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = не скомпилированы в собственном коде<br /><br /> 1 = скомпилированы в собственном коде<br /><br /> Значение по умолчанию — 0.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.system_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-sql-modules-transact-sql.md)   
 [Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
