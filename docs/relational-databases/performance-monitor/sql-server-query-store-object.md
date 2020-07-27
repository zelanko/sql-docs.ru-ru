---
title: SQL Server, объект хранилища запросов | Документация Майкрософт
description: Сведения об объекте хранилища запросов, который предоставляет счетчики, позволяющие отслеживать использование ресурсов SQL Server для хранения текстов запросов, планов выполнения и статистики времени выполнения.
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Query Store object
- SQL Server:Query Store
ms.assetid: b4a04acd-0b66-44a5-b72d-1a45b49e13e6
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 28a4a3a1711a72f7944dc48b12add759160d1dc9
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458758"
---
# <a name="sql-server-query-store-object"></a>SQL Server, объект хранилища запросов

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Объект хранилища запросов предоставляет счетчики, позволяющие отслеживать использование ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения текстов запросов, планов выполнения и статистики времени выполнения для таких объектов, как хранимые процедуры, динамические и подготовленные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и триггеры.  
  
В таблице ниже описаны счетчики **хранилища запросов SQL Server**.  
  
|Счетчики хранилища запросов SQL Server|Описание|  
|-------------------------------------|-----------------|  
|**Счетчик использования ЦП для хранилища запросов**|Указывает использование ЦП хранилищем запросов в качестве процентиля использования ЦП другими процессами.|  
|**Счетчик логических операций чтения хранилища запросов**|Показывает количество логических операций чтения, выполненных хранилищем запросов.|  
|**Счетчик логических операций записи хранилища запросов**|Показывает объем данных, которые помещаются в очередь для удаления из хранилища запросов. Частота и задержка добавления элементов в очередь (что представляет статистику времени выполнения) контролируются параметром интервала сброса данных.|  
|**Счетчик физических операций чтения хранилища запросов**|Показывает количество физических операций чтения, выполненных хранилищем запросов.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр хранилища запросов|Описание|  
|--------------------------|-----------------|  
|**_Total**|Сведения о хранилище запросов для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|\<database name>|Сведения о хранилище запросов для этой базы данных.|  
  
## <a name="see-also"></a>См. также:  

- [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Хранимые процедуры хранилища запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)
- [Представления каталога хранилища запросов (Transact-SQL)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)
- [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
