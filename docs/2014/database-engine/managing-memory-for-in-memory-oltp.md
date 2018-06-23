---
title: Управление памятью для OLTP в памяти | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 365d51004820d3b8c18a9f7667e1328d5bc10143
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098717"
---
# <a name="managing-memory-for-in-memory-oltp"></a>Управление памятью для компонента In-Memory OLTP
  Оптимизированные для памяти таблицы требуют наличия достаточного объема памяти для хранения всех строк и индексов в памяти. Поскольку память является ограниченным ресурсом, важно понимать принципы управления загруженностью памяти в системе. Темы в этом разделе описывают распространенные сценарии использования и управления памятью.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-------------|-----------------|  
|[Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Оценка потребностей таблиц в памяти.|  
|[Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|Пошаговое руководство для связывания базы данных с пулом ресурсов.|  
|[Мониторинг и устранение неполадок с использованием памяти](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|Средства, с помощью которых можно контролировать использование памяти. Также описывается устранение неполадок при слишком сильной загрузке памяти.|  
|[Устранение проблем нехватки памяти](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|Шаги для устранения ситуаций, возникающих из-за нехватки памяти (OOM - Out of Memory).|  
|[Восстановление базы данных и ее привязка к пулу ресурсов](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|Шаги для восстановления базы данных [!INCLUDE[hek_2](../includes/hek-2-md.md)] и ее привязки к именованному пулу ресурсов.|  
|[Сборка мусора для выполняемой в памяти OLTP](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|Общие сведения о сборке мусора для удаленных строк.|  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  