---
title: "Объект метаданных каталога (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6397e547f46c68c29a70739ccaff2be8edd51416
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, объект метаданных каталога
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

