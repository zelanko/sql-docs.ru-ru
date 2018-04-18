---
title: sys.dm_pdw_exec_connections (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: cc03edbacfc9e760536a6599fc7f1ae6520e3c81
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о соединениях, установленных с данным экземпляром [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], и подробные сведения о каждом соединении.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Идентифицирует сеанс, связанный с данным соединением. Используйте `SESSION_ID()` для возврата `session_id` текущего соединения.|  
|connect_time|**datetime**|Метка времени установления соединения. Не допускает значение NULL.|  
|encrypt_option|**nvarchar(40)**|Указывает значение TRUE (соединение зашифровано) или ЛОЖЬ (соединение не enctypred).|  
|auth_scheme|**nvarchar(40)**|Указывает схему проверки подлинности ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Windows), используемую с данным соединением. Не допускает значение NULL.|  
|client_id|**varchar(48)**|IP-адрес клиента, подключающегося к серверу. Допускает значение NULL.|  
|sql_spid|**int**|Идентификатор серверного процесса соединения. Используйте `@@SPID` для возврата `sql_spid` текущего соединения. Для наиболее одновременно, используйте `session_id` вместо него.|  
  
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
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

