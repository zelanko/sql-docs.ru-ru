---
title: sys.dm_pdw_exec_connections (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7bafa5e91cbf8237b1e0b20ea40d79a471ca7978
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36886590"
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о соединениях, установленных с данным экземпляром [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], и подробные сведения о каждом соединении.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Идентифицирует сеанс, связанный с данным соединением. Используйте `SESSION_ID()` для возврата `session_id` текущего соединения.|  
|connect_time|**datetime**|Метка времени установления соединения. Не допускает значение NULL.|  
|encrypt_option|**nvarchar(40)**|Возвращает значение true (соединение зашифровано) или FALSE (соединение не enctypred).|  
|auth_scheme|**nvarchar(40)**|Указывает схему проверки подлинности ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Windows), используемую с данным соединением. Не допускает значение NULL.|  
|client_id|**varchar(48)**|IP-адрес клиента, подключающегося к этому серверу. Допускает значение NULL.|  
|sql_spid|**int**|Идентификатор процесса сервера соединения. Используйте `@@SPID` для возврата `sql_spid` текущего соединения. Для наиболее применять для других целей, используйте `session_id` вместо этого.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется **VIEW SERVER STATE** разрешение на сервере.  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|Один к одному|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|Многие к одному|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Типичный запрос для сбора сведений о собственном соединении запросов.  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

