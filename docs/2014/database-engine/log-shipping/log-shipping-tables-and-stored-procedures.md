---
title: Таблицы доставки журналов и хранимые процедуры | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- monitor servers [SQL Server]
- log shipping [SQL Server], system tables
- log shipping [SQL Server], stored procedures
- primary servers [SQL Server]
ms.assetid: 03420810-4c38-4c0c-adf0-913eb044c50a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d88e0826617b63638c720f176da84a85d68a7e18
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087684"
---
# <a name="log-shipping-tables-and-stored-procedures"></a>Log Shipping Tables and Stored Procedures
  В этом подразделе описываются все таблицы и хранимые процедуры, связанные с конфигурированием доставки журналов. Все таблицы доставки журналов хранятся в базе данных **msdb** на каждом сервере. В приведенной ниже таблице показано, на каких серверах используются какие таблицы и хранимые процедуры в конфигурациях доставки журналов.  
  
## <a name="primary-server-tables"></a>Таблицы сервера-источника  
  
|Таблица|Описание|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Содержит идентификатор задания предупреждения. Данная таблица используется на сервере-источнике только в том случае, если удаленный сервер мониторинга не настроен.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Сохраняет описание ошибки заданий доставки журналов, связанных с сервером-источником.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Сохраняет подробные данные журнала для заданий доставки журналов, связанных с сервером-источником.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Содержит одну запись монитора для данной базы данных-источника.|  
|[log_shipping_primary_databases](/sql/relational-databases/system-tables/log-shipping-primary-databases-transact-sql)|Содержит сведения о конфигурации баз данных-источников на заданном сервере. Хранит по одной строке на каждую базу данных-источник.|  
|[log_shipping_primary_secondaries](/sql/relational-databases/system-tables/log-shipping-primary-secondaries-transact-sql)|Сопоставляет базы данных-источники с базами данных-получателями.|  
  
## <a name="primary-server-stored-procedures"></a>Хранимые процедуры сервера-источника  
  
|Хранимая процедура|Описание|  
|----------------------|-----------------|  
|[sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)|Настраивает базу данных-источник для конфигурации доставки журналов, включая задания резервного копирования, запись локального монитора и запись удаленного монитора.|  
|[sp_add_log_shipping_primary_secondary, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql)|Добавляет имя базы данных-получателя к существующей базе данных-источнику.|  
|[sp_change_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql)|Изменяет настройки базы данных-источника, включая локальные и удаленные записи монитора.|  
|[sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|Производит очистку журнала локально и на сервере мониторинга с учетом срока хранения.|  
|[sp_delete_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql)|Удаляет доставку журналов базы данных-источника, включая как задачи резервного копирования, так и местную, и удаленную подробную информацию журнала.|  
|[sp_delete_log_shipping_primary_secondary, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql)|Удаляет имя базы данных-получателя из базы данных-источника.|  
|[sp_help_log_shipping_primary_database, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)|Получает настройки базы данных-источника и отображает значения из таблиц **log_shipping_primary_databases** и **log_shipping_monitor_primary** .|  
|[sp_help_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql)|Получает имена баз данных-получателей для базы данных-источника.|  
|[sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|Обновляет монитор данными для определенного агента доставки журналов.|  
  
## <a name="secondary-server-tables"></a>Таблицы сервера-получателя  
  
|Таблица|Описание|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Содержит идентификатор задания предупреждения. Данная таблица используется на сервере-получателе только в том случае, если удаленный сервер мониторинга не настроен.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Сохраняет описание ошибки задач доставки журналов, связанных с сервером-получателем.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Сохраняет подробные данные журналов для заданий доставки журналов, связанных с сервером-получателем.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Содержит одну запись монитора для каждой базы данных-получателя, связанной с данным сервером-получателем.|  
|[log_shipping_secondary](/sql/relational-databases/system-tables/log-shipping-secondary-transact-sql)|Содержит сведения о конфигурации баз данных-получателей на заданном сервере. Хранит по одной строке на каждый идентификатор базы данных-получателя.|  
|[log_shipping_secondary_databases](/sql/relational-databases/system-tables/log-shipping-secondary-databases-transact-sql)|Сохраняет сведения о конфигурации для заданной базы данных-получателя. Хранит по одной строке на каждую базу данных-получатель.|  
  
> [!NOTE]  
>  Базы данных-получатели на одном и том же сервере-получателе для заданной базы данных-источника выкладывают настройки для общего пользования в таблицу **log_shipping_secondary** . Если общие настройки изменяются одной базой данных-получателем, то эти изменения относятся сразу ко всем этим базам данных.  
  
## <a name="secondary-server-stored-procedures"></a>Хранимые процедуры сервера-получателя  
  
|Хранимая процедура|Описание|  
|----------------------|-----------------|  
|[sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql)|Устанавливает базу данных-получателя для доставки журналов.|  
|[sp_add_log_shipping_secondary_primary, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql)|Настраивает первичные данные, добавляет ссылки на локальные и удаленные мониторы, а также создает задания копирования и восстановления на сервере-получателе для указанной базы данных-источника.|  
|[sp_change_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql)|Изменяет настройки базы данных-получателя, включая местные и удаленные записи монитора.|  
|[sp_change_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-primary-transact-sql)|Изменяет настройки базы данных-получателя, такие как исходный и целевой каталоги и срок хранения файла.|  
|[sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|Производит очистку журнала локально и на сервере мониторинга с учетом срока хранения.|  
|[sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql)|Удаляет базу данных-получателя, а также локальный и удаленный журналы.|  
|[sp_delete_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-primary-transact-sql)|Удаляет сведения об определенном сервере-источнике из сервера-получателя.|  
|[sp_help_log_shipping_secondary_database, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)|Получает настройки базы данных-получателя из таблиц **log_shipping_secondary**, **log_shipping_secondary_databases**и **log_shipping_monitor_secondary** .|  
|[sp_help_log_shipping_secondary_primary, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql)|Эта хранимая процедура получает настройки для данной базы данных-источника с сервера-получателя.|  
|[sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|Обновляет монитор данными для определенного агента доставки журналов.|  
  
## <a name="monitor-server-tables"></a>Таблицы сервера мониторинга  
  
|Таблица|Описание|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Содержит идентификатор задания предупреждения.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Сохраняет подробное описание ошибок для заданий доставки журналов.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Сохраняет подробные данные журнала для заданий доставки журналов.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Содержит одну запись монитора для каждой базы данных-источника, связанной с данным сервером мониторинга.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Содержит одну запись монитора для каждой базы данных-получателя, связанной с данным сервером мониторинга.|  
  
## <a name="monitor-server-stored-procedures"></a>Хранимые процедуры сервера мониторинга  
  
|Хранимая процедура|Описание|  
|----------------------|-----------------|  
|[sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql)|Создает задание предупреждения доставки журналов, если оно еще не создано.|  
|[sp_delete_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql)|Удаляет задание предупреждения доставки журналов, если отсутствуют соответствующие базы данных-получатели.|  
|[sp_help_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql)|Возвращает идентификатор задания предупреждения.|  
|[sp_help_log_shipping_monitor_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)|Возвращает записи монитора для указанной базы данных-источника из таблицы **log_shipping_monitor_primary** .|  
|[sp_help_log_shipping_monitor_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)|Возвращает записи монитора для указанной базы данных-получателя из таблицы **log_shipping_monitor_secondary** .|  
  
  
