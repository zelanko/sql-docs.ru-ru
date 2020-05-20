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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5ebb27860d7b7da46680a61486c59de3929117ce
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834237"
---
# <a name="sp_tables_ex-transact-sql"></a>sp_tables_ex (Transact-SQL)
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
`[ @table_server = ] 'table_server'`Имя связанного сервера, для которого возвращаются сведения о таблице. Аргумент *table_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
``[ , [ @table_name = ] 'table_name']``Имя таблицы, для которой возвращаются сведения о типе данных. Аргумент *table_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_schema = ] 'table_schema']`Схема таблицы. Аргумент *table_schema*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Имя базы данных, в которой находится указанный *table_name* . Аргумент *table_catalog* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_type = ] 'table_type'`Тип возвращаемой таблицы. Аргумент *TABLE_TYPE* имеет тип **sysname**, значение по умолчанию NULL и может иметь одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**ПСЕВДОНИМ**|Имя псевдонима.|  
|**GLOBAL TEMPORARY**|Имя временной таблицы, доступной в пределах системы.|  
|**LOCAL TEMPORARY**|Имя временной таблицы, доступной только для текущего задания.|  
|**SYNONYM**|Имя синонима.|  
|**СИСТЕМНАЯ ТАБЛИЦА**|Имя системной таблицы.|  
|**СИСТЕМНОЕ ПРЕДСТАВЛЕНИЕ**|Имя системного представления.|  
|**Таблица**|Имя пользовательской таблицы.|  
|**РЕЖИМЕ**|Имя представления.|  
  
`[ @fUsePattern = ] 'fUsePattern'`Определяет, будут ли символы **_**, **%** , **[** и **]** интерпретироваться как подстановочные знаки. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *фусепаттерн* имеет **бит**и значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы. Различные продукты СУБД поддерживают имена таблиц (_Квалификаторы_**,** состоящие из трех частей). _владелец_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых других СУБД он представляет имя сервера в среде баз данных, где находится таблица. Это поле может иметь значение NULL.|  
|**TABLE_SCHEM**|**sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**TABLE_NAME**|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**TABLE_TYPE**|**varchar (32)**|Таблица, системная таблица или представление.|  
|**ЗАМЕЧАНИЯ**|**varchar (254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
  
## <a name="remarks"></a>Remarks  
 **sp_tables_ex** выполняется путем запроса набора строк TABLES интерфейса **IDBSchemaRowset** поставщика OLE DB, соответствующего *table_server*. Параметры *table_name*, *table_schema*, *table_catalog*и *столбцов* передаются этому интерфейсу для ограничения возвращаемых строк.  
  
 **sp_tables_ex** возвращает пустой результирующий набор, если поставщик OLE DB указанного связанного сервера не поддерживает набор строк TABLES интерфейса **IDBSchemaRowset** .  
  
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
 [Хранимые процедуры распределенных запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
