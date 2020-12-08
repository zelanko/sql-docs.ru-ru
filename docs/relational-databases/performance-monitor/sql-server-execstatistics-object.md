---
title: Объект статистики выполнения (SQL Server) | Документация Майкрософт
description: Сведения об объекте SQLServer:ExecStatistics, который предоставляет счетчики для контроля над различными выполнениями.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 67ef3667057a2cb5e2507d89a515814d2ea427e6
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505742"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server, объект ExecStatistics
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
  
  
