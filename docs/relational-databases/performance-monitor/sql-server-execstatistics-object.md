---
title: "Объект статистики выполнения (SQL Server) | Документация Майкрософт"
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
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 709d44983ef7010b36de6238ce99b2d20397017a
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-execstatistics-object"></a>SQL Server, объект ExecStatistics
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
  
  
