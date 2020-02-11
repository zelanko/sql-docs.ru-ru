---
title: log_shipping_monitor_secondary (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_secondary_TSQL
- log_shipping_monitor_secondary
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_secondary system table
ms.assetid: afbe1bb7-89a7-4020-9408-0af64a043c2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 838c810c28c03ae11237f449483789ed8dbbf740
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67989957"
---
# <a name="log_shipping_monitor_secondary-transact-sql"></a>log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной записи монитора для каждой базы данных-получателя в конфигурации доставки журналов. Эта таблица хранится в базе данных **msdb** .  
  
 Таблицы, связанные с ведением журналов и мониторингом, также используются на сервере-источнике и серверах-получателях.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**secondary_server**|**имеет sysname**|Имя дополнительного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов.|  
|**secondary_database**|**имеет sysname**|Имя базы данных-получателя в конфигурации доставки журналов.|  
|**secondary_id**|**UNIQUEIDENTIFIER**|Идентификатор сервера-получателя в конфигурации доставки журналов.|  
|**primary_server**|**имеет sysname**|Имя первичного экземпляра компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журнала.|  
|**primary_database**|**имеет sysname**|Имя базы данных-источника в конфигурации доставки журналов.|  
|**restore_threshold**|**int**|Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение.|  
|**threshold_alert**|**int**|Предупреждение, создаваемое при истечении порогового срока восстановления.|  
|**threshold_alert_enabled**|**bit**|Этот аргумент определяет, активированы ли предупреждения об истечении порогового срока восстановления. 1 = включено.<br /><br /> 0 = отключено.|  
|**last_copied_file**|**nvarchar (500)**|Имя последнего файла резервной копии, скопированного на сервер-получатель.|  
|**last_copied_date**|**datetime**|Дата и время последней операции копирования на сервер-получатель.|  
|**last_copied_date_utc**|**datetime**|Дата и время последней операции копирования на сервер-получатель по времени в формате UTC.|  
|**last_restored_file**|**nvarchar (500)**|Имя файла последней резервной копии, восстановленной в базу данных-получатель.|  
|**last_restored_date**|**datetime**|Дата и время последней операции восстановления в базе данных-получателе.|  
|**last_restored_date_utc**|**datetime**|Дата и время последней операции восстановления в базу данных-получатель по времени в формате UTC.|  
|**last_restored_latency**|**int**|Время (в минутах), прошедшее от создания резервной копии журналов в базе данных-источнике до ее восстановления в базу данных-получатель.<br /><br /> Исходное значение равно NULL.|  
|**history_retention_period**|**int**|Время (в минутах) хранения истории доставки журналов для конкретной базы данных-получателя; по истечении этого времени записи удаляются.|  
  
## <a name="remarks"></a>Remarks  
 Помимо сохранения на удаленном сервере мониторинга, сведения, связанные с сервером-получателем, также хранятся на сервере-получателе в своей **log_shipping_monitor_secondary** таблице.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [Системные таблицы &#40;&#41;Transact-SQL](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
