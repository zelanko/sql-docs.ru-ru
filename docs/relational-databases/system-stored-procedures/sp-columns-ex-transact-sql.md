---
title: sp_columns_ex (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_columns_ex
- sp_columns_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns_ex
ms.assetid: c12ef6df-58c6-4391-bbbf-683ea874bd81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77608294b06025d5c265e67f71f9b0b228732729
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85871105"
---
# <a name="sp_columns_ex-transact-sql"></a>sp_columns_ex (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о столбцах для указанных таблиц связанного сервера по одной строке на столбец. **sp_columns_ex** возвращает сведения о столбце только для определенного столбца, если указан *столбец* .  
  
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
`[ @table_server = ] 'table_server'`Имя связанного сервера, для которого возвращаются сведения о столбцах. Аргумент *table_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @table_name = ] 'table_name'`Имя таблицы, для которой возвращаются сведения о столбцах. Аргумент *table_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_schema = ] 'table_schema'`Имя схемы таблицы, для которой возвращаются сведения о столбцах. Аргумент *table_schema* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Имя каталога таблицы, для которой возвращаются сведения о столбцах. Аргумент *table_catalog* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @column_name = ] 'column'`Имя столбца базы данных, для которого необходимо указать сведения. *столбец* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @ODBCVer = ] 'ODBCVer'`Используемая версия ODBC. *Одбквер* имеет **тип int**и значение по умолчанию 2. Это значение соответствует ODBC версии 2. Допустимы значения 2 или 3. Сведения о различиях между версиями 2 и 3 см. в спецификации ODBC SQLColumns.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы или представления. Различные продукты СУБД поддерживают имена таблиц (_Квалификаторы_**,** состоящие из трех частей). _владелец_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица. Это поле может иметь значение NULL.|  
|**TABLE_SCHEM**|**sysname**|Имя владельца таблицы или представления. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, который создал таблицу. Это поле всегда возвращает значение.|  
|**TABLE_NAME**|**sysname**|Имя таблицы или представления. Это поле всегда возвращает значение.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца возвращаемого **table_name** . Это поле всегда возвращает значение.|  
|**DATA_TYPE**|**smallint**|Целочисленное значение, соответствующий индикатор типа ODBC. Если это тип данных, который не может быть сопоставлен с типом данных ODBC, возвращается значение NULL. Имя собственного типа данных возвращается в столбец **TYPE_NAME** .|  
|**TYPE_NAME**|**varchar (** 13 **)**|Тип данных в символьном представлении. Название типа предоставляется базовой СУБД.|  
|**COLUMN_SIZE**|**int**|Количество значащих цифр. Возвращаемое значение для столбца **точности** находится в базовом 10.|  
|**BUFFER_LENGTH**|**int**|Размер буфера при передаче данных.|  
|**DECIMAL_DIGITS**|**smallint**|Число цифр справа от десятичной запятой.|  
|**NUM_PREC_RADIX**|**smallint**|Основание системы счисления для числовых типов данных.|  
|**ОБНУЛЯЕМОГО**|**smallint**|Указывает возможность содержать значение NULL.<br /><br /> 1 = значение NULL допустимо.<br /><br /> 0 = значение NULL недопустимо.|  
|**ЗАМЕЧАНИЯ**|**varchar (** 254 **)**|Это поле всегда возвращает значение NULL.|  
|**COLUMN_DEF**|**varchar (** 254 **)**|Значение столбца по умолчанию.|  
|**SQL_DATA_TYPE**|**smallint**|Значение типа данных SQL в том же виде, что и в поле TYPE дескриптора. Этот столбец аналогичен столбцу **data_type** , за исключением типов данных **DateTime** и SQL-92 **Interval** . Этот столбец всегда возвращает значение.|  
|**SQL_DATETIME_SUB**|**smallint**|Код подтипа для типов данных **DateTime** и SQL-92 **Interval** . Для других типов данных этот столбец возвращает значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина столбца символьного или целочисленного типа в байтах. Для всех других типов данных этот столбец возвращает значение NULL.|  
|**ORDINAL_POSITION**|**int**|Порядковый номер столбца в таблице. Первый столбец в таблице имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
|**IS_NULLABLE**|**varchar (** 254 **)**|Способность столбца таблицы содержать значение NULL. Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO SQL, не может вернуть пустую строку.<br /><br /> YES = Столбец может содержать значение NULL.<br /><br /> NO = Столбец не может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Значение, возвращаемое для этого столбца, отличается от значения, возвращаемого для столбца, **допускающего значение NULL** .|  
|**SS_DATA_TYPE**|**tinyint**|Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемый расширенными хранимыми процедурами.|  
  
 Дополнительные сведения см. в документации по Microsoft ODBC.  
  
## <a name="remarks"></a>Комментарии  
 **sp_columns_ex** выполняется путем запроса набора строк COLUMNS интерфейса **IDBSchemaRowset** поставщика OLE DB, соответствующего *table_server*. Параметры *table_name*, *table_schema*, *table_catalog*и *столбцов* передаются этому интерфейсу для ограничения возвращаемых строк.  
  
 **sp_columns_ex** возвращает пустой результирующий набор, если поставщик OLE DB указанного связанного сервера не поддерживает набор строк COLUMNS интерфейса **IDBSchemaRowset** .  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="remarks"></a>Комментарии  
 **sp_columns_ex** соответствует требованиям для идентификаторов с разделителями. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается тип данных для столбца `JobTitle` в таблице `HumanResources.Employee` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на связанном сервере `Seattle1`.  
  
```  
EXEC sp_columns_ex 'Seattle1',   
   'Employee',   
   'HumanResources',   
   'AdventureWorks2012',   
   'JobTitle';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
