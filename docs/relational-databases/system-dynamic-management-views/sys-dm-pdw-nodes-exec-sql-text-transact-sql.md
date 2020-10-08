---
title: sys.dm_pdw_nodes_exec_sql_text (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, возвращающее текст пакета SQL, идентифицируемого указанным sql_handle.
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
ms.openlocfilehash: b03cb78d4ccdfa7e7d70a82a1709fe961da0a93c
ms.sourcegitcommit: 32135463a8494d9ed1600a58f51819359e3c09dc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2020
ms.locfileid: "91834204"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys.pdw_nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Возвращает текст пакета SQL, идентифицируемого указанным *sql_handle*. Функция с табличным значением заменяет системную функцию **fn_get_sql**.  
   
## <a name="table-returned"></a>Таблица возвращена  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Уникальный числовой идентификатор, связанный с узлом.|
|**DBID**|**smallint**|Идентификатор базы данных.<br /><br /> Для незапланированных и подготовленных инструкций SQL — идентификатор базы данных, в которой были скомпилированы инструкции.|  
|**objectid**|**int**|Идентификатор объекта.<br /><br /> Имеет значение NULL для нерегламентированных и подготовленных инструкций SQL.|  
|**number**|**smallint**|Для пронумерованной хранимой процедуры этот столбец возвращает ее номер. Дополнительные сведения см. в разделе [sys.numbered_procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Имеет значение NULL для нерегламентированных и подготовленных инструкций SQL.|  
|**Шифрование**|**bit**|1: текст SQL зашифрован.<br /><br /> 0: текст SQL не зашифрован.|  
|**text**|**nvarchar(max)**|Текст SQL-запроса.<br /><br /> Имеет значение NULL для зашифрованных объектов.|  

## <a name="remarks"></a>Комментарии  
Те же примечания в [sys.dm_exec_sql_text](./sys-dm-exec-sql-text-transact-sql.md?view=sql-server-ver15) применяются.  
  
## <a name="permissions"></a>Разрешения  
 Требуется роль сервера **sysadmin** или `VIEW SERVER STATE` разрешение на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные советы по разработке см. в статье [Проектные решения и методики программирования для хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).