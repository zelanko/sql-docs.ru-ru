---
title: "sp_columns_ex (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_columns_ex
- sp_columns_ex_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_columns_ex
ms.assetid: c12ef6df-58c6-4391-bbbf-683ea874bd81
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 90ba287e14dc19afef8e19be65c81337c653fe48
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spcolumnsex-transact-sql"></a>sp_columns_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о столбцах для указанных таблиц связанного сервера по одной строке на столбец. **sp_columns_ex** возвращает сведения о столбцах только определенный столбец, если *столбца* указано.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_columns_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_server =** ] **"***table_server***"**  
 Имя связанного сервера, для которого возвращаются сведения о столбцах. *table_server* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@table_name =** ] **"***table_name***"**  
 Имя таблицы, для которой возвращаются сведения о столбцах. *имя_таблицы* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_schema =** ] **"***table_schema***"**  
 Имя схемы таблицы, для которой возвращаются сведения о столбцах. *table_schema* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_catalog =** ] **"***значениям table_catalog***"**  
 Имя каталога таблицы, для которой возвращаются сведения о столбцах. *значениям table_catalog* — **sysname**, значение по умолчанию NULL.  
  
 [  **@column_name =** ] **"***столбца***"**  
 Имя столбца базы данных, для которого возвращаются сведения. *столбец* — **sysname**, значение по умолчанию NULL.  
  
 [  **@ODBCVer =** ] **"***Аргумент ODBCVer***"**  
 Версия используемого протокола ODBC. *Аргумент ODBCVer* — **int**, значение по умолчанию 2. Это значение соответствует ODBC версии 2. Допустимы значения 2 или 3. Сведения о различиях между версиями 2 и 3 см. в спецификации ODBC SQLColumns.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы или представления. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*квалификатор***.** *владельца***.** *имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица. Это поле может иметь значение NULL.|  
|**ПО ЗНАЧЕНИЯМ TABLE_SCHEM**|**sysname**|Имя владельца таблицы или представления. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, который создал таблицу. Это поле всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы или представления. Это поле всегда возвращает значение.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца **TABLE_NAME** возвращается. Это поле всегда возвращает значение.|  
|**ТИП ДАННЫХ**|**smallint**|Целочисленное значение, соответствующий индикатор типа ODBC. Если это тип данных, который не может быть сопоставлен с типом данных ODBC, возвращается значение NULL. Собственное имя типа данных возвращается в **TYPE_NAME** столбца.|  
|**TYPE_NAME**|**varchar (**13**)**|Тип данных в символьном представлении. Название типа предоставляется базовой СУБД.|  
|**COLUMN_SIZE**|**int**|Количество значащих цифр. Возвращаемое значение для **точности** столбец имеет десятичную форму.|  
|**BUFFER_LENGTH**|**int**|Размер буфера при передаче данных.|  
|**DECIMAL_DIGITS**|**smallint**|Число цифр справа от десятичной запятой.|  
|**NUM_PREC_RADIX**|**smallint**|Основание системы счисления для числовых типов данных.|  
|**ДОПУСКАЮЩИЕ ЗНАЧЕНИЯ NULL**|**smallint**|Указывает возможность содержать значение NULL.<br /><br /> 1 = значение NULL допустимо.<br /><br /> 0 = значение NULL недопустимо.|  
|**ПРИМЕЧАНИЯ**|**varchar (**254**)**|Это поле всегда возвращает значение NULL.|  
|**COLUMN_DEF**|**varchar (**254**)**|Значение столбца по умолчанию.|  
|**SQL_DATA_TYPE**|**smallint**|Значение типа данных SQL в том же виде, что и в поле TYPE дескриптора. Этот столбец содержит то же, как **DATA_TYPE** столбца, за исключением **datetime** и SQL-92 **интервал** типов данных. Этот столбец всегда возвращает значение.|  
|**SQL_DATETIME_SUB**|**smallint**|Код подтипа для **datetime** и SQL-92 **интервал** типов данных. Для других типов данных этот столбец возвращает значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина столбца символьного или целочисленного типа в байтах. Для всех других типов данных этот столбец возвращает значение NULL.|  
|**ORDINAL_POSITION**|**int**|Порядковый номер столбца в таблице. Первый столбец в таблице имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
|**IS_NULLABLE**|**varchar (**254**)**|Способность столбца таблицы содержать значение NULL. Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO SQL, не может вернуть пустую строку.<br /><br /> YES = Столбец может содержать значение NULL.<br /><br /> NO = Столбец не может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Возвращаемое значение для этого столбца отличается от значения, возвращаемого в **NULLABLE** столбца.|  
|**SS_DATA_TYPE**|**tinyint**|Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемый расширенными хранимыми процедурами.|  
  
 Дополнительные сведения см. в документации по Microsoft ODBC.  
  
## <a name="remarks"></a>Замечания  
 **sp_columns_ex** выполняется путем запроса СТОЛБЦОВ набора строк **IDBSchemaRowset** интерфейса поставщика OLE DB, соответствующий *table_server*. *Table_name*, *table_schema*, *значениям table_catalog*, и *столбца* параметры передаются этому интерфейсу для ограничения строк возвращается.  
  
 **sp_columns_ex** возвращает пустой результирующий набор, если поставщик OLE DB указанного связанного сервера не поддерживает набор строк COLUMNS **IDBSchemaRowset** интерфейса.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="remarks"></a>Замечания  
 **sp_columns_ex** соответствует требованиям для идентификаторов с разделителями. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается тип данных для столбца `JobTitle` в таблице `HumanResources.Employee` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на связанном сервере `Seattle1`.  
  
```  
EXEC sp_columns_ex 'Seattle1',   
   'Employee',   
   'HumanResources',   
   'AdventureWorks2012',   
   'JobTitle';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_foreignkeys &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
