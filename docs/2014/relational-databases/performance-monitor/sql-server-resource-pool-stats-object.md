---
title: SQL Server, объект статистики пула ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Reosurce Pool Stats object
- 'SQLServer: Resource Pool Stats object'
ms.assetid: bb46e029-fcf9-4aeb-a066-be41e7668fb9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5fdf00d1291180197f66cd6cb23cf27f10659c68
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183018"
---
# <a name="sql-server-resource-pool-stats-object"></a>SQL Server, объект Resource Pool Stats
  Объект SQLServer:Resource Pool Stats содержит счетчики производительности, сообщающие основные данные статистики пула ресурсов регулятора ресурсов.  
  
 Каждый активный пул ресурсов создает экземпляр объекта производительности SQLServer:Resource Pool Stats, при этом имя экземпляра совпадает с именем пула ресурсов в регуляторе ресурсов. В следующей таблице описываются счетчики, поддерживаемые этим экземпляром.  
  
|Имя счетчика|Description|  
|------------------|-----------------|  
|Загрузка ЦП, %|Использование пропускной способности ЦП всеми группами рабочей нагрузки, принадлежащими данному пулу. Измеряется относительно рабочего компьютера и нормализуется по всем процессорам системы. Это значение будет изменено при изменении количества ЦП, доступных для процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оно не нормализовано по отношению к значению, получаемому процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|CPU usage target %|Целевое значение параметра загрузки ЦП для пула ресурсов, рассчитанное на основании параметров конфигурации пула ресурсов и загрузки системы.|  
|CPU control effect %|Воздействие регулятора ресурсов на пул ресурсов. Рассчитывается по формуле: (Загрузка ЦП, %)/(Загрузка ЦП, %, без регулятора ресурсов).|  
|Compile memory target (KB)|Текущее значение целевого брокера памяти для компиляции запросов, в килобайтах (КБ).|  
|Cache memory target (KB)|Текущее значение целевого брокера памяти для кэширования, в килобайтах (КБ).|  
|Query exec memory target (KB)|Текущее значение целевого брокера памяти для предоставления памяти на выполнение запросов, в килобайтах (КБ). Эта информация также доступна в представлении [sys.dm_exec_query_memory_grants](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql).|  
|Memory grants/sec|Число операций предоставления памяти, выполняемых в данном пуле ресурсов за одну секунду.|  
|Active memory grants count|Текущее общее количество операций по предоставлению памяти. Эта информация также доступна в представлении [sys.dm_exec_query_memory_grants](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql).|  
|Memory grant timeouts/sec|Количество операций предоставления памяти с истекшим временем ожидания за секунду.|  
|Active memory grant amount (KB)|Текущий суммарный объем предоставленной памяти, в килобайтах (КБ). Эта информация также доступна в представлении [sys.dm_exec_query_resource_semaphores](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql).|  
|Pending memory grant count|Число запросов на предоставление памяти, ожидающих в очереди. Эта информация также доступна в представлении [sys.dm_exec_query_resource_semaphores](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql).|  
|Max memory (KB)|Максимальный объем памяти в килобайтах (КБ), которым может располагать пул ресурсов; рассчитывается на основе заданных параметров пула ресурсов и состояния сервера.|  
|Used memory (KB)|Объем используемой памяти в пуле ресурсов, в килобайтах (КБ).|  
|Target memory (KB)|Целевой объем памяти, в килобайтах (КБ), который пул ресурсов пытается получить. Рассчитывается на основе заданных параметров пула ресурсов и состояния сервера.|  
|Операций чтения с диска/с|Количество операций чтения с диска в течение последней секунды.|  
|Регулированных операций ввода-вывода чтения с диска/с|Количество операций чтения, регулированных в течение последней секунды.|  
|Скорость чтения с диска (байт/с) |Число байтов, прочитанных с диска в течение последней секунды.|  
|Ср. вр. чт. с диска (мс)|Среднее время (в миллисекундах) операции чтения с диска.|  
|Операции записи на диск/с|Количество операций записи на диск в течение последней секунды.|  
|Регулированные операции ввода-вывода записи на диск/с|Количество операций записи, регулированных в течение последней секунды.|  
| Скорость записи на диск (байт/с)|Число байтов, записанных на диск в течение последней секунды.|  
|Ср. вр. записи на диск (мс)|Среднее время (мс) операции записи на диск.|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг использования ресурсов &#40;системном мониторе&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, объект статистики группы рабочей нагрузки](sql-server-workload-group-stats-object.md)   
 [Регулятор ресурсов](../resource-governor/resource-governor.md)  
  
  
