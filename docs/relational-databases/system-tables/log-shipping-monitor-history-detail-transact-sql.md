---
title: log_shipping_monitor_history_detail (Transact-SQL) | Документы Microsoft
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
- log_shipping_monitor_history_detail_TSQL
- log_shipping_monitor_history_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_history_detail system table
ms.assetid: 7080c888-323b-4206-a1ab-e6c51f9e2579
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0e028134b1afd16122efee2b3e4316be73d4098d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="logshippingmonitorhistorydetail-transact-sql"></a>log_shipping_monitor_history_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сохраняет подробные данные журнала для заданий доставки журналов. Эта таблица хранится в **msdb** базы данных.  
  
 Таблицы, связанные с ведением журналов и мониторингом, также используются на сервере-источнике и серверах-получателях.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|Первичный идентификатор для резервирования или вторичный идентификатор для копирования или восстановления.|  
|**agent_type**|**tinyint**|Тип задания доставки журналов:<br /><br /> 0 = резервирование;<br /><br /> 1 = копирование;<br /><br /> 2 = восстановление.|  
|**session_id**|**int**|Идентификатор сеанса для задания резервирования/копирования/восстановления.|  
|**database_name**|**sysname**|Имя базы данных, связанной с данной записью. База данных-источник для резервирования, база данных-получатель для восстановления или пустая для копирования.|  
|**session_status**|**tinyint**|Состояние сеанса.<br /><br /> 0 = начало.<br /><br /> 1 = запуск.<br /><br /> 2 = успешно.<br /><br /> 3 = ошибка.<br /><br /> 4 = предупреждение.|  
|**log_time**|**datetime**|Дата и время создания записи.|  
|**log_time_utc**|**datetime**|Дата и время создания записи по Гринвичу.|  
|**message**|**nvarchar(max)**|Текст сообщения.|  
  
## <a name="remarks"></a>Замечания  
 Эта таблица содержит подробное описание агентов доставки журналов. Чтобы идентифицировать сеанс агента, используйте столбцы **agent_id**, **agent_type**, и **session_id**. Чтобы просмотреть подробные данные журнала для сеанса агента, отсортируйте их по **log_time**.  
  
 Помимо хранения на удаленном сервере мониторинга, хранятся сведения, связанные с сервера-источника на сервере-источнике в его **log_shipping_monitor_history_detail** таблицы и сведения, относящиеся к получателю сервер также хранится на сервере-получателе в его **log_shipping_monitor_history_detail** таблицы.  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [Системные таблицы &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [log_shipping_monitor_error_detail &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql.md)  
  
  
