---
title: sp_tables_ex (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 44ffbbfdac8e1976df99be35ecbed7dd94e3ee61
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745442"
---
# <a name="sptablesex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает табличные данные о таблицах на указанном связанном сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_server=** ] **"***table_server***"**  
 Имя связанного сервера, для которого необходимо вернуть сведения о таблице. *table_server* — **sysname**, не имеет значения по умолчанию.  
  
 [ **,** [  **@table_name=** ] **"***table_name***"**]  
 Имя таблицы, для которой необходимо вернуть сведения о типе данных. *TABLE_NAME*— **sysname**, значение по умолчанию NULL.  
  
 [  **@table_schema=** ] **"***table_schema***"**]  
 Схема таблицы. *table_schema*— **sysname**, значение по умолчанию NULL.  
  
 [  **@table_catalog=** ] **"***значениям table_catalog***"**  
 Имя базы данных, в котором указанный *table_name* находится. *значениям table_catalog* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_type=** ] **"***table_type***"**  
 Возвращаемый тип таблицы. *TABLE_TYPE* — **sysname**, значение по умолчанию NULL и может иметь одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**ПСЕВДОНИМ**|Имя псевдонима.|  
|**ГЛОБАЛЬНУЮ ВРЕМЕННУЮ**|Имя временной таблицы, доступной в пределах системы.|  
|**ЛОКАЛЬНЫЙ ВРЕМЕННЫЙ**|Имя временной таблицы, доступной только для текущего задания.|  
|**SYNONYM**|Имя синонима.|  
|**СИСТЕМНАЯ ТАБЛИЦА**|Имя системной таблицы.|  
|**СИСТЕМНОЕ ПРЕДСТАВЛЕНИЕ**|Имя системного представления.|  
|**TABLE**|Имя пользовательской таблицы.|  
|**VIEW**|Имя представления.|  
  
 [  **@fUsePattern=** ] **"***шаблонов***"**  
 Определяет, является ли символы **_**, **%**, **[**, и **]** интерпретируются как символы-шаблоны. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *Шаблонов* — **бит**, значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*квалификатор ***.*** владелец ***.*** имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых других СУБД он представляет имя сервера в среде баз данных, где находится таблица. Это поле может иметь значение NULL.|  
|**ПО ЗНАЧЕНИЯМ TABLE_SCHEM**|**sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**TABLE_TYPE**|**varchar(32)**|Таблица, системная таблица или представление.|  
|**"ПРИМЕЧАНИЯ"**|**varchar(254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
  
## <a name="remarks"></a>Примечания  
 **sp_tables_ex** выполняется путем запроса набора строк TABLES **IDBSchemaRowset** интерфейс поставщика OLE DB, соответствующий *table_server*. *Table_name*, *table_schema*, *значениям table_catalog*, и *столбец* параметры передаются этому интерфейсу для ограничения строк возвращается.  
  
 **sp_tables_ex** возвращает пустой результирующий набор, если поставщик OLE DB указанного связанного сервера не поддерживает набор строк TABLES **IDBSchemaRowset** интерфейс.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается информация о таблицах, содержащихся в схеме `HumanResources` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], расположенной на связанном сервере `LONDON2`.  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>См. также  
 [Распределенные запросы, хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
