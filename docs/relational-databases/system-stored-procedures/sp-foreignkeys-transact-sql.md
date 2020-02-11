---
title: sp_foreignkeys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_foreignkeys_TSQL
- sp_foreignkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_foreignkeys
ms.assetid: 935fe385-19ff-41a4-8d0b-30618966991d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c1aaa12ed6ffb86b6e3f7979deac0e6f933dff8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124380"
---
# <a name="sp_foreignkeys-transact-sql"></a>sp_foreignkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает внешние ключи, ссылающиеся на первичные ключи в таблице на связанном сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_foreignkeys [ @table_server = ] 'table_server'   
     [ , [ @pktab_name = ] 'pktab_name' ]   
     [ , [ @pktab_schema = ] 'pktab_schema' ]   
     [ , [ @pktab_catalog = ] 'pktab_catalog' ]   
     [ , [ @fktab_name = ] 'fktab_name' ]   
     [ , [ @fktab_schema = ] 'fktab_schema' ]   
     [ , [ @fktab_catalog = ] 'fktab_catalog' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @table_server = ] 'table_server'`Имя связанного сервера, для которого возвращаются сведения о таблице. Аргумент *table_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @pktab_name = ] 'pktab_name'`Имя таблицы с первичным ключом. Аргумент *pktab_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @pktab_schema = ] 'pktab_schema'`Имя схемы с первичным ключом. Аргумент *pktab_schema*имеет тип **sysname**и значение по умолчанию NULL. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] здесь содержится имя владельца.  
  
`[ @pktab_catalog = ] 'pktab_catalog'`Имя каталога с первичным ключом. Аргумент *pktab_catalog*имеет тип **sysname**и значение по умолчанию NULL. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] здесь содержится имя базы данных.  
  
`[ @fktab_name = ] 'fktab_name'`Имя таблицы с внешним ключом. Аргумент *fktab_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @fktab_schema = ] 'fktab_schema'`Имя схемы с внешним ключом. Аргумент *fktab_schema*имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @fktab_catalog = ] 'fktab_catalog'`Имя каталога с внешним ключом. Аргумент *fktab_catalog*имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
 Различные продукты СУБД поддерживают имена таблиц, состоящие из трех частей (_Catalog_)**.** _схема_**.** _Table_), представленного в результирующем наборе.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**PKTABLE_CAT**|**имеет sysname**|Каталог для таблицы, в котором находится первичный ключ.|  
|**PKTABLE_SCHEM**|**имеет sysname**|Схема для таблицы, в которой находится первичный ключ.|  
|**PKTABLE_NAME**|**имеет sysname**|Имя таблицы (с первичным ключом). Это поле всегда возвращает значение.|  
|**PKCOLUMN_NAME**|**имеет sysname**|Имя первичного ключевого столбца или столбцов для каждого столбца возвращаемого **table_name** . Это поле всегда возвращает значение.|  
|**FKTABLE_CAT**|**имеет sysname**|Каталог для таблицы, в котором находится внешний ключ.|  
|**FKTABLE_SCHEM**|**имеет sysname**|Схема для таблицы, в которой находится внешний ключ.|  
|**FKTABLE_NAME**|**имеет sysname**|Имя таблицы (с внешним ключом). Это поле всегда возвращает значение.|  
|**FKCOLUMN_NAME**|**имеет sysname**|Имена внешних ключевых столбцов для каждого возвращаемого столбца TABLE_NAME. Это поле всегда возвращает значение.|  
|**KEY_SEQ**|**smallint**|Порядковый номер столбца в первичном ключе, состоящем из нескольких столбцов. Это поле всегда возвращает значение.|  
|**UPDATE_RULE**|**smallint**|Действие, совершаемое над внешним ключом, когда операция SQL является операцией обновления. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает 0, 1 или 2 для этих столбцов:<br /><br /> 0=CASCADE; каскадное изменение в соответствии с внешним ключом.<br /><br /> 1=NO ACTION; отсутствие изменений при наличии внешнего ключа.<br /><br /> 2=SET_NULL; установка значения внешнего ключа в NULL.|  
|**DELETE_RULE**|**smallint**|Действие, совершаемое над внешним ключом, когда операция SQL является операцией удаления. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает 0, 1 или 2 для этих столбцов:<br /><br /> 0=CASCADE; каскадное изменение в соответствии с внешним ключом.<br /><br /> 1=NO ACTION; отсутствие изменений при наличии внешнего ключа.<br /><br /> 2=SET_NULL; установка значения внешнего ключа в NULL.|  
|**FK_NAME**|**имеет sysname**|Идентификатор внешнего ключа. Возвращает NULL, если не применим к источнику данных. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает имя ограничения FOREIGN KEY.|  
|**PK_NAME**|**имеет sysname**|Идентификатор первичного ключа. Возвращает NULL, если не применим к источнику данных. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает имя ограничения PRIMARY KEY.|  
|**DEFERRABILITY**|**smallint**|Указывает, допускается ли задержка проверки ограничений.|  
  
 В результирующем наборе столбцы FK_NAME и PK_NAME всегда возвращают NULL.  
  
## <a name="remarks"></a>Remarks  
 **sp_foreignkeys** запрашивает набор строк FOREIGN_KEYS интерфейса **IDBSchemaRowset** поставщика OLE DB, соответствующего *table_server*. Параметры *table_name*, *table_schema*, *table_catalog*и *столбцов* передаются этому интерфейсу для ограничения возвращаемых строк.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается информация внешнего ключа о таблице `Department` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на связанном сервере `Seattle1`.  
  
```  
EXEC sp_foreignkeys @table_server = N'Seattle1',   
   @pktab_name = N'Department',   
   @pktab_catalog = N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
