---
title: "sys.dm_hadr_auto_page_repair (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_hadr_auto_page_repair_TSQL
- sys.dm_hadr_auto_page_repair
- sys.dm_hadr_auto_page_repair_TSQL
- dm_hadr_auto_page_repair
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- automatic page repair
- sys.dm_hadr_auto_page_repair dynamic management view
ms.assetid: d7840adf-4a1b-41ac-bc94-102c07ad1c79
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ec6bf44d2628247af4d132cf06aadd30a19ceaf
ms.sourcegitcommit: 6e016a4ffd28b09456008f40ff88aef3d911c7ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
# <a name="sysdmhadrautopagerepair-transact-sql"></a>sys.dm_hadr_auto_page_repair (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждой попытки автоматического восстановления страниц во всех базах данных доступности в реплике доступности, размещенной в группе доступности на экземпляре сервера. Это представление содержит строки, связанные с последними попытками автоматического восстановления страниц в определенной базе данных-источнике или получателе, количество которых ограничено числом в 100 строк на каждую базу данных. По достижении максимального значения строка для следующей попытки автоматического восстановления страниц заменяет одну из существующих записей.
  
  В следующей таблице определены значения различных столбцах:  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, которой принадлежит строка.|  
|**file_id**|**int**|Идентификатор файла, в котором находится страница.|  
|**page_id**|**bigint**|Идентификатор страницы в файле.|  
|**error_type**|**int**|Тип ошибки. Допустимые значения:<br /><br /> **-**1 = все ошибки 823 оборудования<br /><br /> 1 = 824 ошибки, кроме неверной контрольной сумме или обрыву страницы (например, неверный идентификатор страницы)<br /><br /> 2 = неверная контрольная сумма;<br /><br /> 3 = разрыв страницы.|  
|**page_status**|**int**|Состояние попытки восстановления страниц:<br /><br /> 2 = в очереди на запрос к участнику;<br /><br /> 3 = запрос отправлен участнику;<br /><br /> 4 = в очереди на автоматическое восстановление страниц (от участника получен ответ);<br /><br /> 5 = автоматическое восстановление страниц успешно завершено, и страница должна быть готова к использованию;<br /><br /> 6 = непоправимо повреждена. Во время попытки восстановления страниц произошла ошибка, например потому, что страница также повреждена на участнике, или участник не подключен, или возникли проблемы с сетью. Это состояние не окончательное: если на странице вновь встретится повреждение, она будет запрошена у участника.|  
|**modification_time**|**datetime**|Время последнего изменения состояния страницы.|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Автоматическое восстановление страниц (группы доступности: зеркальное отображение баз данных)](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [suspect_pages &#40; Transact-SQL &#41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [Управление таблицей suspect_pages (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  

