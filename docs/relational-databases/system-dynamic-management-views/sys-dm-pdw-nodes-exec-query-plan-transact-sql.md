---
title: sys. DM _pdw_nodes_exec_query_plan (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, возвращающее инструкцию Showplan в формате XML для пакета, указанного в маркере плана. План, указанный в дескрипторе плана может быть кэширован или выполняться в данный момент.
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
ms.openlocfilehash: 96b499ea5bc38d2a4cf9c380116108009ea46086
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145639"
---
# <a name="syspdw_nodes_dm_exec_query_plan-transact-sql"></a>sys. PDW _nodes_dm_exec_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Возвращает события инструкции Showplan в XML-формате для пакета, указанного в дескрипторе плана. План, указанный в дескрипторе плана может быть кэширован или выполняться в данный момент.  

## <a name="table-returned"></a>Таблица возвращена  
  
|Имя столбца|Data type|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Уникальный числовой идентификатор, связанный с узлом.| 
|**dbid**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для незапланированных и подготовленных инструкций SQL — идентификатор базы данных, в которой были скомпилированы инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**objectid**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец имеет **значение NULL**.<br /><br /> Столбец может содержать значение NULL.|  
|**number**|**smallint**|Целое число нумерованных хранимых процедур. Для нерегламентированных и подготовленных пакетов этот столбец имеет **значение NULL**.<br /><br /> Столбец может содержать значение NULL.| 
|**Шифрование**|**бит**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**xml**;|Содержит представление Showplan времени компиляции для плана выполнения запроса, указанного в параметре *plan_handle*. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.|  
  
## <a name="remarks"></a>Remarks  
Те же примечания в [sys. DM _exec_query_plan](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql?view=sql-server-ver15) применяются.  
  
## <a name="permissions"></a>Permissions  
 Требуется роль сервера **sysadmin** или разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="see-also"></a>См. также раздел  
 [Динамические административные представления &#40;хранилища данных SQL и параллельного хранилища данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>Следующие шаги
 Дополнительные советы по разработке см. в статье [Общие сведения о разработке хранилища данных SQL](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).