---
title: sys. DM _pdw_nodes_exec_sql_text (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, возвращающее текст пакета SQL, идентифицируемого по заданной sql_handle.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: fd886217b2fb2caf0fe3f32e88b7bf0215ece1a9
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145679"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys. PDW _nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Возвращает текст пакета SQL, идентифицируемого по заданной *sql_handle*. Эта возвращающая табличное значение функция заменяет системную функцию **fn_get_sql**.  
   
## <a name="table-returned"></a>Таблица возвращена  
|Имя столбца|Data type|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Уникальный числовой идентификатор, связанный с узлом.|
|**dbid**|**smallint**|Идентификатор базы данных.<br /><br /> Для незапланированных и подготовленных инструкций SQL — идентификатор базы данных, в которой были скомпилированы инструкции.|  
|**objectid**|**int**|Идентификатор объекта.<br /><br /> Имеет значение NULL для нерегламентированных и подготовленных инструкций SQL.|  
|**number**|**smallint**|Для пронумерованной хранимой процедуры этот столбец возвращает ее номер. Дополнительные сведения см. в разделе [sys. &#40;NUMBERED_PROCEDURES Transact-&#41;SQL](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Имеет значение NULL для нерегламентированных и подготовленных инструкций SQL.|  
|**Шифрование**|**бит**|1: текст SQL зашифрован.<br /><br /> 0: текст SQL не зашифрован.|  
|**text**|**nvarchar(max)**|Текст SQL-запроса.<br /><br /> Имеет значение NULL для зашифрованных объектов.|  

## <a name="remarks"></a>Remarks  
Те же примечания в [представлении sys. DM _exec_sql_text](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql?view=sql-server-ver15) применяются.  
  
## <a name="permissions"></a>Permissions  
 Требуется роль сервера **sysadmin** или разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также раздел  
 [Динамические административные представления &#40;хранилища данных SQL и параллельного хранилища данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Следующие шаги
 Дополнительные советы по разработке см. в статье [Общие сведения о разработке хранилища данных SQL](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).