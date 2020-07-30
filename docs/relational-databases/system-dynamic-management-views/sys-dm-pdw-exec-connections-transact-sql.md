---
title: sys. dm_pdw_exec_connections (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 74cfb2819cd462a2e3cf695cbb0daf92b4dac5a3
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87332387"
---
# <a name="sysdm_pdw_exec_connections-transact-sql"></a>sys. dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Возвращает сведения о соединениях, установленных с данным экземпляром [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], и подробные сведения о каждом соединении.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Идентифицирует сеанс, связанный с данным соединением. Используйте `SESSION_ID()` для возврата `session_id` текущего соединения.|  
|connect_time|**datetime**|Метка времени установления соединения. Не допускает значение NULL.|  
|encrypt_option|**nvarchar(40)**|Указывает TRUE (соединение зашифровано) или FALSE (соединение не енктипред).|  
|auth_scheme|**nvarchar(40)**|Указывает схему проверки подлинности ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Windows), используемую с данным соединением. Не допускает значение NULL.|  
|client_id|**varchar(48)**|IP-адрес клиента, подключающегося к серверу. Допускает значение NULL.|  
|sql_spid|**int**|Идентификатор серверного процесса соединения. Используйте `@@SPID` для возврата `sql_spid` текущего соединения. Для большинства целей используйте `session_id` вместо.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **View Server State** на сервере.  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
| От | Кому | Связь |
| ---- | -- | ------------ |
|dm_pdw_exec_sessions. session_id|dm_pdw_exec_connections. session_id|Один к одному|  
|dm_pdw_exec_requests. connection_id|dm_pdw_exec_connections. connection_id|Многие к одному|  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
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
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

