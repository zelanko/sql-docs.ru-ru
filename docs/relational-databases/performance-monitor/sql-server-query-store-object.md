---
title: SQL Server, объект хранилища запросов | Документация Майкрософт
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
ms.openlocfilehash: 620e79cd69c11c6f5de32d3ef0ae97af489f9398
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304845"
---
# <a name="sql-server-query-store-object"></a>SQL Server, объект хранилища запросов

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
|\<имя базы данных>|Сведения о хранилище запросов для этой базы данных.|  
  
## <a name="see-also"></a>См. также:  

- [Мониторинг производительности с использованием хранилища запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Хранимые процедуры хранилища запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)
- [Представления каталога хранилища запросов (Transact-SQL)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)
- [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
