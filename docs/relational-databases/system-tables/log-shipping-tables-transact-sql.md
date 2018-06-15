---
title: Таблицы (Transact-SQL) для доставки журналов | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- log shipping [SQL Server], system tables
- system tables [SQL Server], log shipping
ms.assetid: f8910aae-2013-4645-880c-134577cbcbe0
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2311c021121fb2b5a6f8f7581b298d1f61bb857e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261320"
---
# <a name="log-shipping-tables-transact-sql"></a>Таблицы доставки журналов (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Следующие разделы описывают системные таблицы, которые хранят данные, используемые операциями доставки журналов.  
  
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
  
  
