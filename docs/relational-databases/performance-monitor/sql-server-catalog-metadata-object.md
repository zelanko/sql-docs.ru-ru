---
title: Объект метаданных каталога (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 484dc0c7be3b7ca67c3645e6b8f088839d4bf631
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950509"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, объект метаданных каталога
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Объект производительности **SQLServer:Catalog Metadata** предоставляет счетчики для метаданных каталога SQL Server.

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
