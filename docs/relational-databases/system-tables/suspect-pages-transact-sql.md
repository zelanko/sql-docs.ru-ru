---
title: suspect_pages (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- suspect_page_table
- suspect_page_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- suspect_pages system table
- suspect pages [SQL Server]
ms.assetid: 119c8d62-eea8-44fb-bf72-de469c838c50
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6719ef53c60491e3f0445abc0eb2e6fa20dcd8ea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="suspectpages-transact-sql"></a>suspect_pages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке на каждую страницу, с незначительная ошибка 823 или 824 ошибки. Список содержит все строки, подозреваемые на наличие ошибок. Некоторые из них могут быть исправными. После исправления подозрительной страницы его состояние обновляется в **event_type** столбца.  
  
 В следующей таблице, в которой существует ограничение в 1000 строк, хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, которой принадлежит страница.|  
|**file_id**|**int**|Идентификатор файла в базе данных.|  
|**page_id**|**bigint**|Идентификатор подозрительной страницы. Каждая страница имеет идентификатор страницы, который является 32-разрядным значением, определяющим расположение страницы в базе данных. **Page_id** — это смещение в файле данных 8-Килобайтной страницы. Каждый идентификатор страницы уникален в пределах файла.|  
|**event_type**|**int**|Тип ошибки; один из следующих.<br /><br /> 1 = ошибка 823, не относящаяся к странице (например, ошибка чтения диска), либо ошибка 824, относящаяся к неверной контрольной сумме или обрыву страницы (например, идентификатор страницы).<br /><br /> 2 = неверная контрольная сумма.<br /><br /> 3 = обрыв страницы.<br /><br /> 4 = восстановленная (страница была восстановлена после того, как была помечена как неверная).<br /><br /> 5 = исправленная (страница исправлена инструкцией DBCC).<br /><br /> 7 = освобождена инструкцией DBCC.|  
|**error_count**|**int**|Количество ошибок.|  
|**last_update_date**|**datetime**|Метка даты и времени последнего обновления.|  
  
## <a name="permissions"></a>Разрешения  
 Сведения в таблице **suspect_pages** доступны любому пользователю, имеющему доступ к базе данных **msdb** . Информация в таблице suspect_pages может обновляться любым пользователем, обладающим разрешением UPDATE. Члены предопределенной роли базы данных **db_owner** в **msdb** или предопределенной роли сервера **sysadmin** могут вставлять, обновлять и удалять записи.  
  
## <a name="see-also"></a>См. также  
 [Восстановление страниц (SQL Server)](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [Класс событий страницы Database Suspect Data](../../relational-databases/event-classes/database-suspect-data-page-event-class.md)   
 [Системные таблицы &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [Управление таблицей suspect_pages (SQL Server)](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
