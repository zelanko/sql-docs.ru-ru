---
title: sys.dm_exec_input_buffer (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8531f33f2d027eba14d4416e9138560b25ead20e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013136"
---
# <a name="sysdmexecinputbuffer-transact-sql"></a>sys.dm_exec_input_buffer (Transact-SQL)
[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

  Возвращает сведения об инструкциях, отправленных в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_exec_input_buffer ( session_id , request_id )
```  
  
## <a name="arguments"></a>Аргументы  
*session_id*  
Идентификатор сеанса выполнения пакета выполняется поиск. *session_id* — **smallint**. *session_id* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)   
  
*request_id*  
Идентификатор request_id из [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). *Идентификатор request_id* — **int**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**event_type**|**nvarchar(256)**|Тип события во входном буфере для заданной spid.|  
|**parameters**|**smallint**|Любые параметры, предоставленные для инструкции.|  
|**event_info**|**nvarchar(max)**|Текст инструкции во входном буфере для заданной spid.|  
  
## <a name="permissions"></a>Разрешения  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если пользователь имеет разрешение VIEW SERVER STATE, пользователь увидит все выполняющиеся сеансы на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; в противном случае пользователь будет видеть только текущий сеанс.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)], если пользователь является владельцем базы данных, пользователь увидит все выполняющиеся сеансы на [!INCLUDE[ssSDS](../../includes/sssds-md.md)]; в противном случае пользователь будет видеть только текущий сеанс.  
  
## <a name="remarks"></a>Примечания  
 Данная функция динамического управления может использоваться в сочетании с sys.dm_exec_sessions или sys.dm_exec_requests во время работы **CROSS APPLY**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example"></a>A. Простой пример  
 Ниже приведен пример, передавая идентификатор сеанса (SPID) и идентификатор запроса функции.  
  
```sql  
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```  
  
### <a name="b-using-cross-apply-to-additional-information"></a>Б. С помощью кросс-применяются на дополнительные сведения  
 В следующем примере перечисляются входного буфера для сеансов с идентификатором сеанса, больше 50.  
  
```sql  
SELECT es.session_id, ib.event_info   
FROM sys.dm_exec_sessions AS es  
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib  
WHERE es.session_id > 50;
GO
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [DBCC INPUTBUFFER (Transact-SQL)](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
