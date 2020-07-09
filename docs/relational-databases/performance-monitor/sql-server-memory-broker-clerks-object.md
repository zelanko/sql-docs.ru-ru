---
title: SQL Server, объект клерков брокера памяти | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 5a14877c98b4abb2487712cfed2bd744c20933d2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775817"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, объект клерков брокера памяти
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Объект производительности **SQLServer:Memory Broker Clerks** предоставляет счетчики для сбора статистики по клеркам брокера памяти.

В следующей таблице представлены объекты производительности **Memory Broker Clerks** SQL Server.

|**SQL Server, счетчики клерков брокера памяти**|Description|  
|-------------|-----------------|  
|**Внутреннее преимущество**|Внутреннее значение нехватки памяти в миллисекундах на страницу, умноженное на 10 миллиардов и округленное до целого числа.|
|**Размер клерка брокера памяти**|Размер клерка памяти в страницах.|
|**Периодические вытеснения (страниц)**|Число страниц, удаленных из клерка брокера при последнем периодическом удалении.|
|**Вытеснения с давлением (стр/с)**|Число страниц в секунду, удаляемых из клерка брокера из-за нехватки памяти.|
|**Преимущества эмуляции**|Значение клерка памяти в миллисекундах на страницу, умноженное на 10 миллиардов и округленное до целого числа.|
|**Размер эмуляции**|Текущий размер эмуляции клерка в страницах.|

Существует экземпляр счетчика для буферного пула и для пула объектов хранилища столбцов.

## <a name="see-also"></a>См. также:  
[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
