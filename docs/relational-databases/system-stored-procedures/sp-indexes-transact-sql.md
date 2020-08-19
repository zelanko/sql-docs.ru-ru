---
description: sp_indexes (Transact-SQL)
title: sp_indexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_indexes_TSQL
- sp_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexes
ms.assetid: 25469e72-9d95-463f-912a-193471c8f5e2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6129240ab59b3629704a4d67fb80b4306d6bb621
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446977"
---
# <a name="sp_indexes-transact-sql"></a>sp_indexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает индексную информацию для указанной удаленной таблицы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_indexes [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_db' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @table_server =] "*table_server*"  
 Имя связанного сервера с запущенным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого запрашиваются сведения о таблице. Аргумент *table_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @table_name =] "*table_name*"  
 Имя удаленной таблицы, для которой возвращаются сведения об индексе. Аргумент *table_name* имеет тип **sysname**и значение по умолчанию NULL. Если NULL, возвращаются все таблицы указанной базы данных.  
  
 [ @table_schema =] "*table_schema*"  
 Задает схему таблицы. В среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствует владельцу таблицы. Аргумент *table_schema* имеет тип **sysname**и значение по умолчанию NULL.  
  
 [ @table_catalog =] "*table_db*"  
 Имя базы данных, в которой находится *table_name* . Аргумент *table_db* имеет тип **sysname**и значение по умолчанию NULL. Если значение равно NULL, *table_db* значение по умолчанию — **master**.  
  
 [ @index_name =] "*index_name*"  
 Имя индекса, для которого запрашиваются сведения. Аргумент *index* имеет тип **sysname**и значение по умолчанию NULL.  
  
 [ @is_unique =] "*is_unique*"  
 Тип индекса, для которого запрашиваются сведения. *is_unique* является **битным**, имеет значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|1|Возвращает сведения об уникальных индексах.|  
|0|Возвращает сведения об неуникальных индексах.|  
|NULL|Возвращает сведения обо всех индексах.|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|TABLE_CAT|**sysname**|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|**sysname**|Схема для таблицы.|  
|TABLE_NAME|**sysname**|Имя удаленной таблицы.|  
|NON_UNIQUE|**smallint**|Является ли индекс уникальным или неуникальным:<br /><br /> 0 = уникальное<br /><br /> 1 = неуникальное|  
|INDEX_QUALIFER|**sysname**|Имя владельца индекса. В некоторых СУБД пользователям, не являющимся владельцами таблицы, разрешено создавать индексы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец всегда совпадает с **table_name**.|  
|INDEX_NAME|**sysname**|Имя индекса.|  
|TYPE|**smallint**|Тип индекса:<br /><br /> 0 = статистика по таблице<br /><br /> 1 = кластеризованный<br /><br /> 2 = хэшированный<br /><br /> 3 = другие|  
|ORDINAL_POSITION|**int**|Порядковый номер столбца в индексе. Номер первого столбца в таблице равен 1. Этот столбец всегда возвращает значение.|  
|COLUMN_NAME|**sysname**|Соответствующее имя столбца для каждого столбца возвращенной TABLE_NAME.|  
|ASC_OR_DESC|**varchar**|Порядок, используемые в параметрах сортировки:<br /><br /> A = по возрастанию<br /><br /> D = по убыванию<br /><br /> NULL = неприменимо<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает A.|  
|CARDINALITY|**int**|Число строк в таблице или уникальных значений в индексе.|  
|PAGES|**int**|Число страниц для хранения индекса или таблицы.|  
|FILTER_CONDITION|**nvarchar (** 4000 **)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все сведения об индексе из таблицы `Employees` базы данных `AdventureWorks2012` на связанном сервере `Seattle1`.  
  
```  
EXEC sp_indexes @table_server = 'Seattle1',   
   @table_name = 'Employee',   
   @table_schema = 'HumanResources',  
   @table_catalog = 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры распределенных запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
