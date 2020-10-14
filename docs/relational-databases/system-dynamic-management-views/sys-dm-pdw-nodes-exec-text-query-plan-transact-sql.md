---
title: sys.dm_pdw_nodes_exec_text_query_plan (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, возвращающее инструкцию Showplan в текстовом формате для пакета TSQL или для конкретной инструкции в пакете.
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
ms.openlocfilehash: 5ac37e8c768068244c549d28d9bf6d157d46e853
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035298"
---
# <a name="sysdm_pdw_nodes_exec_text_query_plan--transact-sql"></a>sys.dm_pdw_nodes_exec_text_query_plan (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Возвращает инструкцию Showplan в текстовом формате для пакета [!INCLUDE[tsql](../../includes/tsql-md.md)] или для определенной инструкции в пакете.

## <a name="table-returned"></a>Таблица возвращена  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pdw_node_ID**|**int**|Уникальный числовой идентификатор, связанный с узлом.|
|**DBID**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**objectid**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец содержит значение **NULL**.<br /><br /> Столбец может содержать значение NULL.|  
|**number**|**smallint**|Целое число нумерованных хранимых процедур. Для нерегламентированных и подготовленных пакетов этот столбец содержит значение **NULL**.<br /><br /> Столбец может содержать значение NULL.| 
|**Шифрование**|**bit**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**nvarchar(max)**|Содержит представление Showplan времени компиляции для плана выполнения запроса, указанного в *plan_handle*. Инструкция Showplan имеет текстовый формат. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.|  

## <a name="remarks"></a>Комментарии  
Те же примечания в [sys.dm_exec_text_query_plan](./sys-dm-exec-text-query-plan-transact-sql.md?view=sql-server-ver15) применяются.  

## <a name="permissions"></a>Разрешения  
 Требуется роль сервера **sysadmin** или `VIEW SERVER STATE` разрешение на сервере.  
  
## <a name="see-also"></a>См. также статью  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные советы по разработке см. в статье [Проектные решения и методики программирования для хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).