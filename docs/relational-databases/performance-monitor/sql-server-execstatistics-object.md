---
title: Объект статистики выполнения (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 258aaee37e6e0c6bbbb0a43326a21c80712e9749
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773112"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, объект ExecStatistics
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект **SQLServer:ExecStatistics** в Microsoft SQL Server предоставляет счетчики для контроля над различными выполнениями.  
  
 В этой таблице приведено описание счетчиков **Ведения статистики** SQL Server.  
  
|Счетчики ведения статистики SQL Server|Описание|  
|-----------------------------------------|-----------------|  
|**Распределенный запрос**|Статистика, относящаяся к выполнению распределенных запросов.|  
|**Вызовы DTC**|Статистика, относящаяся к выполнению вызовов DTC.|  
|**Расширенные процедуры**|Статистика, относящаяся к выполнению расширенных процедур.|  
|**Вызовы OLEDB**|Статистика, относящаяся к выполнению вызовов OLEDB.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Элемент|Описание|  
|----------|-----------------|  
|**Среднее время выполнения (сек)**|Среднее время выполнения выбранного типа выполнения.|  
|**Совокупное время выполнения (мс) в секунду**|Агрегированное время выполнения выбранного типа выполнения в секунду.|  
|**Текущие выполняемые задачи**|Количество совершающихся в текущий момент выполнений выбранного типа выполнения.|  
|**Выполнения, запущенные в секунду**|Количество запущенных в секунду выполнений выбранного типа выполнения.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
