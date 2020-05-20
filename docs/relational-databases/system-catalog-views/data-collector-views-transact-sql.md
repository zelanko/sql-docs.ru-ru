---
title: Представления сборщика данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- data collector [SQL Server], views
ms.assetid: a005e885-7813-4c7e-b332-b01d9e9d4054
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6d2df9fd85f77a2fa0207562a5b2a8be3e991489
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823635"
---
# <a name="data-collector-views-transact-sql"></a>Представления сборщика данных (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Тип сборщика данных предоставляет следующие представления для вывода сведений о конфигурации сборщика данных, например свойств сборщика данных, наборов сбора и элементов наборов сбора, а также для вывода статистики выполнения при работе сборщика данных. Эти представления, которые находятся в базе данных **msdb** , также предоставляют уровень абстракции для базовых таблиц. Уровень абстракции повышает безопасность, предотвращая прямой доступ к таблицам и одновременно разрешая изменять таблицы, не затрагивая связанных с ними приложений.  
  
|||  
|-|-|  
|[syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)|[syscollector_collection_sets (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)|  
|[syscollector_collector_types (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)|[syscollector_config_store (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)|  
|[syscollector_execution_log (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-execution-log-transact-sql.md)|[syscollector_execution_log_full (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql.md)|  
|[syscollector_execution_stats (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)||  
  
## <a name="see-also"></a>См. также  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
