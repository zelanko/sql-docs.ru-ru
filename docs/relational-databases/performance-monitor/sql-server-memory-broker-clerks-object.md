---
title: "SQL Server, объект клерков брокера памяти | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
caps.latest.revision: "4"
author: dagiro
ms.author: v-dagir
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4f602e43f585e83158a9a824677b3c73f88e0b87
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, объект клерков брокера памяти
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект производительности **SQLServer:Memory Broker Clerks** предоставляет счетчики для сбора статистики по клеркам брокера памяти.

В следующей таблице представлены объекты производительности **Memory Broker Clerks** SQL Server.

|**SQL Server, счетчики клерков брокера памяти**|Description|  
|-------------|-----------------|  
|**Внутреннее преимущество**|Внутреннее значение нехватки памяти в миллисекундах на страницу, умноженное на 10 миллиардов и округленное до целого числа.|
|**Размер клерка брокера памяти**|Размер клерка в страницах.|
|**Периодические вытеснения (страниц)**|Число страниц, удаленных из клерка брокера при последнем периодическом удалении.|
|**Вытеснения с давлением (стр/с)**|Число страниц в секунду, удаляемых из клерка брокера из-за нехватки памяти.|
|**Преимущества эмуляции**|Значение клерка памяти в миллисекундах на страницу, умноженное на 10 миллиардов и округленное до целого числа.|
|**Размер эмуляции**|Текущий размер эмуляции клерка в страницах.|

Существует экземпляр счетчика для буферного пула и для пула объектов хранилища столбцов.

## <a name="see-also"></a>См. также:  
[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
