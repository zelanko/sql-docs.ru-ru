---
description: Таблицы доставки журналов (Transact-SQL)
title: Таблицы доставки журналов (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- log shipping [SQL Server], system tables
- system tables [SQL Server], log shipping
ms.assetid: f8910aae-2013-4645-880c-134577cbcbe0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b880d19fe1ee01a7b890cc965384beb49efc77cc
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547174"
---
# <a name="log-shipping-tables-transact-sql"></a>Таблицы доставки журналов (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В следующих разделах описываются системные таблицы, в которых хранятся сведения, используемые операциями доставки журналов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [log_shipping_monitor_alert](../../relational-databases/system-tables/log-shipping-monitor-alert-transact-sql.md)  
 Сохраняет идентификаторы предупреждений заданий для доставки журналов.  
  
 [log_shipping_monitor_error_detail](../../relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql.md)  
 Сохраняет подробное описание ошибок для заданий доставки журналов.  
  
 [log_shipping_monitor_history_detail](../../relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql.md)  
 Сохраняет подробные данные журнала для заданий доставки журналов.  
  
 [log_shipping_monitor_primary](../../relational-databases/system-tables/log-shipping-monitor-primary-transact-sql.md)  
 Хранит одну запись монитора для базы данных-источника в каждой конфигурации доставки журналов.  
  
 [log_shipping_monitor_secondary](../../relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql.md)  
 Содержит по одной записи монитора для каждой базы данных-получателя в конфигурации доставки журналов.  
  
 [log_shipping_primary_databases](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
 Сохраняет одну запись для базы данных-источника в конфигурации доставки журналов.  
  
 [log_shipping_primary_secondaries](../../relational-databases/system-tables/log-shipping-primary-secondaries-transact-sql.md)  
 Сопоставляет каждую базу данных-источник с базой данных-получателем.  
  
 [log_shipping_secondary](../../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)  
 Хранит одну запись для каждого вторичного идентификатора.  
  
 [log_shipping_secondary_databases](../../relational-databases/system-tables/log-shipping-secondary-databases-transact-sql.md)  
 Содержит одну запись для каждой базы данных-получателя в конфигурации доставки журнала.  
  
  
