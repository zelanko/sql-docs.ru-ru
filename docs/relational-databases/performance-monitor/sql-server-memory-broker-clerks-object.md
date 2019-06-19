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
manager: craigg
ms.openlocfilehash: e2ae02cd83f99c43f844bdae8da8b7b9860a7769
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62649546"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, объект клерков брокера памяти
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Объект производительности **SQLServer:Memory Broker Clerks** предоставляет счетчики для сбора статистики по клеркам брокера памяти.

В следующей таблице представлены объекты производительности **Memory Broker Clerks** SQL Server.

|**SQL Server, счетчики клерков брокера памяти**|Описание|  
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
