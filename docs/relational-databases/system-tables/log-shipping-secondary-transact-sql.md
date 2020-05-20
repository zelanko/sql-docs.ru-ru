---
title: log_shipping_secondary (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary
- log_shipping_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary system table
ms.assetid: 69723419-4544-49c6-a517-adb30ffa5741
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5debab1572bc2f788c0dc13773d0dc140c693108
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82805997"
---
# <a name="log_shipping_secondary-transact-sql"></a>log_shipping_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Хранит одну запись для каждого вторичного идентификатора. Эта таблица хранится в базе данных **msdb** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**secondary_id**|**uniqueidentifier**|Идентификатор сервера-получателя в конфигурации доставки журналов.|  
|**primary_server**|**sysname**|Имя экземпляра компонента SQL Server Database Engine — источника в конфигурации доставки журналов.|  
|**primary_database**|**sysname**|Имя базы данных-источника в конфигурации доставки журналов.|  
|**backup_source_directory**|**nvarchar (500)**|Каталог, в котором хранятся файлы резервной копии журнала транзакций с сервера-источника.|  
|**backup_destination_directory**|**nvarchar (500)**|Каталог сервера-получателя, в который копируются файлы резервных копий.|  
|**file_retention_period**|**int**|Время в минутах, в течение которого файл резервной копии хранится на сервере-получателе.|  
|**copy_job_id**|**uniqueidentifier**|Идентификатор, назначенный заданию копирования на сервере-получателе.|  
|**restore_job_id**|**uniqueidentifier**|Идентификатор, назначенный заданию восстановления на сервере-получателе.|  
|**monitor_server**|**sysname**|Имя экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], используемого в качестве сервера мониторинга в конфигурации доставки журналов.|  
|**monitor_server_security_mode**|**bit**|Режим безопасности, используемый для подключения к серверу мониторинга:<br /><br /> 1 = проверка подлинности Windows.<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.|  
|**last_copied_file**|**nvarchar (500)**|Имя последнего файла резервной копии, скопированного на сервер-получатель.|  
|**last_copied_date**|**datetime**|Дата и время последней операции копирования на сервер-получатель.|  
  
## <a name="remarks"></a>Примечания  
 Несколько баз данных-получателей на одном вторичном сервере для данной основной базы данных имеют некоторые параметры в таблице **log_shipping_secondary** . Если общий параметр изменяется для одной из них, он изменяется и для всех остальных таких же баз данных.  
  
## <a name="see-also"></a>См. также  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
