---
title: log_shipping_secondary_databases (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary_databases_TSQL
- log_shipping_secondary_databases
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary_databases system table
ms.assetid: ba2374af-86b8-480c-a10c-51e7c4e3ae23
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7f3daf3fa3a2e0873b5f7c62e8b0357cce858ca2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="logshippingsecondarydatabases-transact-sql"></a>log_shipping_secondary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну запись для каждой базы данных-получателя в конфигурации доставки журнала. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**secondary_database**|**sysname**|Имя базы данных-получателя в конфигурации доставки журналов.|  
|**secondary_id**|**uniqueidentifier**|Идентификатор сервера-получателя в конфигурации доставки журналов.|  
|**restore_delay**|**int**|Продолжительность времени, в минутах, в течение которого сервер-получатель будет ждать перед восстановлением данного файла резервной копии. Значение по умолчанию — 0 минут.|  
|**restore_all**|**бит**|Если установлено в 1, то сервер-получатель восстанавливает все доступные резервные копии журналов транзакций при запуске задания восстановления. В противном случае восстанавливается один файл.|  
|**restore_mode**|**бит**|Режим восстановления базы данных-получателя.<br /><br /> 0 = восстановление журнала с аргументом NORECOVERY.<br /><br /> 1 = восстановить журнал в режиме STANDBY.|  
|**disconnect_users**|**бит**|Если установлено в 1, пользователи отключаются от базы данных-получателя при выполнении операции восстановления. Значение по умолчанию 0.|  
|**block_size**|**int**|Размер блока (в байтах) устройства резервного копирования.|  
|**buffer_count**|**int**|Общее число буферов, используемых операцией создания резервной копии или восстановления.|  
|**max_transfer_size**|**int**|Размер в байтах максимального входного или выходного запроса, который выдает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на устройстве резервного копирования.|  
|**last_restored_file**|**nvarchar(500)**|Имя файла последней резервной копии, восстановленной в базу данных-получатель.|  
|**last_restored_date**|**datetime**|Дата и время последней операции восстановления в базе данных-получателе.|  
  
## <a name="see-also"></a>См. также  
 [О доставке журналов & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [log_shipping_secondary (Transact-SQL)](../../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
