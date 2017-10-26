---
title: "Хранилище XTP (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ca13381f6cc2d2b9af6286f28d25791522118a72
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-xtp-storage"></a>Хранилище XTP SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Объект производительности хранилища XTP SQL Server содержит счетчики, относящиеся к дисковому пространству для In-Memory OLTP в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В следующей таблице описаны счетчики **Хранилище XTP SQL Server** .  
  
|Счетчик|Описание|  
|-------------|-----------------|  
|**Закрытые контрольные точки**|Количество закрытых контрольных точек, подсчитанное агентом в сети|  
|**Выполненные контрольные точки**|Количество контрольных точек, обработанных потоком контрольных точек в режиме «вне сети».|  
|**Выполненные основные слияния**|Число основных слияний, выполненных рабочим потоком слияния. Эти слияния по-прежнему требуют установки.|  
|**Оценка политики слияния**|Число оценок политики слияния с момента запуска сервера.|  
|**Незавершенные запросы о слиянии**|Число запросов о слиянии, которые не были выполнены с момента запуска сервера.|  
|**Оставленные слияния**|Количество слияний, оставленных из-за сбоя.|  
|**Установленные слияния**|Число успешно установленных слияний.|  
|**Общее число объединенных файлов**|Общее количество объединенных исходных файлов. С помощью этого количества можно определить среднее число исходных файлов в слиянии.|  
  
## <a name="see-also"></a>См. также:  
 [Счетчики производительности XTP (In-Memory OLTP) для SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  

