---
title: Хранилище XTP (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4ec95b3be82da761292249616e0f81d9527d9f04
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033552"
---
# <a name="sql-server-xtp-storage"></a>Хранилище XTP SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
  
  
