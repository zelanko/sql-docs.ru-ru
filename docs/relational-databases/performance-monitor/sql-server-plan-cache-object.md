---
title: SQL Server, объект Plan Cache | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: f7eaab8804139ea5b7468edc6916fcc07e2374b5
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379916"
---
# <a name="sql-server-plan-cache-object"></a>SQL Server, объект Plan Cache
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект **Plan Cache** содержит счетчики, отслеживающие объем памяти, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения таких объектов, как хранимые процедуры, нерегламентированные и подготовленные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] и триггеры. Параллельно можно отслеживать несколько экземпляров объекта **Plan Cache** , причем в каждом экземпляре могут отслеживаться различные типы плана.  
  
 В приведенной ниже таблице описываются счетчики **SQLServer:Plan Cache**.  
  
|Счетчики объекта Plan Cache|Описание|  
|------------------------------------|-----------------|  
|**Коэффициент попадания в кэш**|Соотношение между числом попаданий в кэш и числом уточняющих запросов.|  
|**Базовый коэффициент попаданий в кэш**|Только для внутреннего применения.| 
|**Счетчик объектов кэша**|Количество объектов в кэше.|  
|**Страницы кэша**|Количество 8-килобайтных страниц, занимаемых объектами кэша.|  
|**Используемых объектов кэша**|Количество используемых объектов кэша.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Экземпляр объекта Plan Cache|Описание|  
|-------------------------|-----------------|  
|**_Total**|Сведения обо всех типах экземпляров кэша.|  
|**Sql Plans**|Планы запросов, формируемые нерегламентированным запросом [!INCLUDE[tsql](../../includes/tsql-md.md)] , включая автоматически параметризованные запросы, либо инструкциями языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , использующими процедуры **sp_prepare** или **sp_cursorprepare**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] кэширует планы нерегламентированных инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] для повторного использования при последующем выполнении идентичных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] . Запросы, параметризованные пользователем (даже в случае, если они не были подготовлены явно) также отображаются в виде подготовленных планов SQL.|  
|**Object Plans**|Планы запроса, формируемые при создании хранимых процедур, функций и триггеров.|  
|**Bound Trees**|Нормализованные деревья для представлений, правил, вычисляемых столбцов и проверочных ограничений.|  
|**Расширенные хранимые процедуры**|Сведения из каталога о расширенных хранимых процедурах.|  
|**Временные таблицы и переменные таблиц**|Сведения из кэша, относящиеся к временным таблицам и табличным переменным.|  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера «Server Memory»](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [SQL Server, объект Buffer Manager](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
