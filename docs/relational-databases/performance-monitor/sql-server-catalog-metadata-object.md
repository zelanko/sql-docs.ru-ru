---
title: "Объект метаданных каталога (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
caps.latest.revision: 
author: dagiro
ms.author: v-dagir
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86913554f86a9965906d37f8a7ff683570dfb8ad
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, объект метаданных каталога
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект производительности **SQLServer:Catalog Metadata** предоставляет счетчики для метаданных каталога SQL Server.

В следующей таблице представлены объекты производительности **Catalog Metadata** SQL Server.


|**Счетчики метаданных каталога для SQL Server**|Description|  
|-------------|-----------------|  
|**Кол-во записей кэша**|Количество записей в кэше метаданных каталога.|
|**Прикреплено записей кэша**|Количество закрепленных записей в кэше метаданных каталога.|
|**Коэффициент попадания в кэш**|Соотношение между количеством попаданий в кэш метаданных каталога и количеством обращений к нему.|
|**Базовый коэффициент попаданий в кэш**|Только для внутреннего применения.|

Для каждой базы данных существует один экземпляр счетчика.

## <a name="see-also"></a>См. также:  
[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
