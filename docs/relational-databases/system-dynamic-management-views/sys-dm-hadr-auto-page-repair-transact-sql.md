---
title: sys.dm_hadr_auto_page_repair (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_auto_page_repair_TSQL
- sys.dm_hadr_auto_page_repair
- sys.dm_hadr_auto_page_repair_TSQL
- dm_hadr_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- automatic page repair
- sys.dm_hadr_auto_page_repair dynamic management view
ms.assetid: d7840adf-4a1b-41ac-bc94-102c07ad1c79
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9d46e5ee0b350e7164c0dfec55666d4b6c8e34a7
ms.sourcegitcommit: 1510d9fce125e5b13e181f8e32d6f6fbe6e7c7fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2019
ms.locfileid: "55771330"
---
# <a name="sysdmhadrautopagerepair-transact-sql"></a>sys.dm_hadr_auto_page_repair (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждой попытки автоматического восстановления страниц во всех базах данных доступности в реплике доступности, размещенной в группе доступности на экземпляре сервера. Это представление содержит строки, связанные с последними попытками автоматического восстановления страниц в определенной базе данных-источнике или получателе, количество которых ограничено числом в 100 строк на каждую базу данных. По достижении максимального значения строка для следующей попытки автоматического восстановления страниц заменяет одну из существующих записей.
  
  В следующей таблице определены значения столбцов:  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, которой принадлежит строка.|  
|**file_id**|**int**|Идентификатор файла, в котором находится страница.|  
|**page_id**|**bigint**|Идентификатор страницы в файле.|  
|**error_type**|**int**|Тип ошибки. Допустимые значения:<br /><br /> **-** 1 = все ошибки 823 оборудования<br /><br /> 1 = 824 ошибки, кроме неверной контрольной сумме или обрыву страницы (например, неверный идентификатор страницы)<br /><br /> 2 = неверная контрольная сумма;<br /><br /> 3 = разрыв страницы.|  
|**page_status**|**int**|Состояние попытки восстановления страниц:<br /><br /> 2 = в очереди на запрос к участнику;<br /><br /> 3 = запрос отправлен участнику;<br /><br /> 4 = страница успешно восстановлена.<br /><br /> 5 = не удалось восстановить страницу во время последней попытки / автоматическое восстановление страниц будет пытаться восстановить страницу еще раз.|  
|**modification_time**|**datetime**|Время последнего изменения состояния страницы.|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Автоматическое восстановление страниц (группы доступности: зеркальное отображение баз данных)](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [suspect_pages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [Управление таблицей suspect_pages (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  

