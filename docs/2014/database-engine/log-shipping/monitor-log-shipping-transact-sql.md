---
title: Наблюдение за доставкой журналов (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], status
- history tables [SQL Server]
- historical information [SQL Server], log shipping
- log shipping [SQL Server], monitoring
- alerts [SQL Server], log shipping
- status information [SQL Server], log shipping
- monitoring log shipping [SQL Server]
ms.assetid: acf3cd99-55f7-4287-8414-0892f830f423
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d480fe510b6d2e252faefaae13d7dd3776c8ec5d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774888"
---
# <a name="monitor-log-shipping-transact-sql"></a>Наблюдение за доставкой журналов (Transact-SQL)
  После того, как была настроена доставка журналов, можно отслеживать данные о состоянии всех серверов доставки журналов. Журнал и состояние операций доставки журналов всегда сохраняются локально заданиями доставки журналов. Журнал и состояние операций резервного копирования сохраняются на сервере-источнике, а журнал и состояние операций копирования и восстановления сохраняются на сервере-получателе. Если был реализован удаленный сервер мониторинга, эти данные также сохраняются и на нем.  
  
 Можно настраивать предупреждения, которые работают в случае сбоев при выполнении операций доставки журналов по расписанию. Сообщения об ошибке создаются заданием предупреждения, отслеживающим состояние операций резервного копирования и восстановления. Можно определить предупреждения, которые отправят сообщение оператору при возникновении таких ошибок. Если сервер мониторинга настроен, то одно задание предупреждения выполняется на нем и отвечает за сообщения об ошибках для всех операций данной конфигурации доставки журналов. Если сервер мониторинга не указан, задание предупреждения выполняется на экземпляре сервера-источника, который отслеживает операции резервного копирования. Если сервер мониторинга не указан, задание предупреждения также выполняется на каждом экземпляре сервера-получателя, где отслеживает локальные операции копирования и восстановления.  
  
> [!IMPORTANT]  
>  Чтобы отслеживать конфигурацию доставки журналов, во время включения доставки журналов необходимо добавить сервер мониторинга. Если добавлять сервер мониторинга позже, то придется удалить существующую конфигурацию доставки журналов и заменить ее новой с сервером мониторинга. Дополнительные сведения см. в разделе [Настройка доставки журналов (SQL Server)](configure-log-shipping-sql-server.md). Кроме того, заданную конфигурацию сервера мониторинга невозможно изменить, не удалив прежде конфигурацию доставки журналов.  
  
## <a name="history-tables-containing-monitoring-information"></a>Таблицы журналов, содержащие данные мониторинга  
 Таблицы журналов мониторинга содержат метаданные, хранящиеся на сервере мониторинга. Копия данных, относящихся именно к данному серверу-источнику или серверу-получателю, также хранится локально.  
  
 Эти таблицы можно опрашивать, чтобы следить за состоянием сеанса доставки журналов. Например, чтобы узнать состояние доставки журналов, можно проверить состояние и историю заданий резервного копирования, копирования и восстановления. Можно просматривать отдельные журналы доставки и подробные сведения об ошибках, выполняя запросы к описанным ниже таблицам мониторинга.  
  
|Таблица|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Содержит идентификатор задания предупреждения.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Содержит подробное описание ошибок заданий доставки журналов. Выполняя запросы к этой таблице, можно получать сведения об ошибках в сеансах агентов. При необходимости можно выполнить сортировку ошибок по дате и времени их внесения в журнал. Каждая ошибка записывается в журнал как последовательность исключений, и на один сеанс агента может приходиться несколько ошибок (последовательностей).|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Содержит подробные журналы агентов доставки журналов. Выполнив запросы к этой таблице, можно получить подробные сведения о предыдущих сеансах агентов.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Содержит одну запись монитора для базы данных-источника в каждой из конфигураций доставки журналов, включая данные о последнем файле резервной копии и о последнем восстановленном файле, которые полезны для мониторинга.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Содержит одну запись монитора для каждой базы данных-получателя, включающую данные о последнем файле резервной копии и последнем восстановленном файле, которые полезны для мониторинга.|  
  
## <a name="stored-procedures-for-monitoring-log-shipping"></a>Хранимые процедуры для мониторинга доставки журналов  
 Сведения мониторинга и данные журналов хранятся в таблицах в базе данных **msdb**, к которым можно получить доступ посредством использования хранимых процедур доставки журналов. Выполняйте эти хранимые процедуры на указанных в следующей таблице серверах.  
  
|Хранимая процедура|Description|Место выполнения процедуры|  
|----------------------|-----------------|---------------------------|  
|[sp_help_log_shipping_monitor_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)|Возвращает записи монитора для указанной базы данных-источника из таблицы **log_shipping_monitor_primary** .|Сервер мониторинга или сервер-источник|  
|[sp_help_log_shipping_monitor_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)|Возвращает записи монитора для указанной базы данных-получателя из таблицы **log_shipping_monitor_secondary** .|Сервер мониторинга или сервер-получатель|  
|[sp_help_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql)|Возвращает идентификатор задания предупреждения.|Сервер мониторинга, сервер-источник или сервер-получатель, если сервер мониторинга не определен.|  
|[sp_help_log_shipping_primary_database, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)|Получает настройки базы данных-источника и отображает значения из таблиц **log_shipping_primary_databases** и **log_shipping_monitor_primary** .|Сервер-источник|  
|[sp_help_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql)|Получает имена баз данных-получателей для базы данных-источника.|Сервер-источник|  
|[sp_help_log_shipping_secondary_database, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)|Получает настройки базы данных-получателя из таблиц **log_shipping_secondary**, **log_shipping_secondary_databases** и **log_shipping_monitor_secondary** .|Сервер-получатель|  
|[sp_help_log_shipping_secondary_primary (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql)|Эта хранимая процедура получает настройки для данной базы данных-источника с сервера-получателя.|Сервер-получатель|  
  
## <a name="see-also"></a>См. также:  
 [Просмотр отчета о доставке журналов (среда SQL Server Management Studio)](view-the-log-shipping-report-sql-server-management-studio.md)   
 [Хранимые процедуры и таблицы доставки журналов](log-shipping-tables-and-stored-procedures.md)  
  
  
