---
title: "SQL Server, объект хранилища запросов | Документация Майкрософт"
ms.custom: 
ms.date: 03/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Store object
- SQL Server:Query Store
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
caps.latest.revision: "8"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 022f801293cb6ede334e0f4b70deceb37777b482
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-query-store-object"></a>SQL Server, объект хранилища запросов
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Объект хранилища запросов предоставляет счетчики, позволяющие отслеживать использование ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения текстов запросов, планов выполнения и статистики времени выполнения для таких объектов, как хранимые процедуры, динамические и подготовленные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и триггеры.  
  
 В таблице ниже описываются счетчики **SQL Server:хранилище запросов**.  
  
|Счетчики хранилища запросов SQL Server|Описание|  
|-------------------------------------|-----------------|  
|**Счетчик использования ЦП для хранилища запросов**|Показывает использование ЦП для хранилища запросов.|  
|**Счетчик логических операций чтения хранилища запросов**|Показывает количество логических операций чтения, выполненных хранилищем запросов.|  
|**Счетчик логических операций записи хранилища запросов**|Показывает объем данных, которые помещаются в очередь для удаления из хранилища запросов. Частота и задержка добавления элементов в очередь (что представляет статистику времени выполнения) контролируются параметром интервала сброса данных.|  
|**Счетчик физических операций чтения хранилища запросов**|Показывает количество физических операций чтения, выполненных хранилищем запросов.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр хранилища запросов|Описание|  
|--------------------------|-----------------|  
|**_Total**|Сведения о хранилище запросов для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|\<имя базы данных>|Сведения о хранилище запросов для этой базы данных.|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Хранимые процедуры в хранилище запросов (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Представления каталога хранилища запросов (Transact-SQL)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
