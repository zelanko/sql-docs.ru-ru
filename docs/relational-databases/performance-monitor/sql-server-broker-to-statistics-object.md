---
title: "SQL Server, объект Broker TO Statistics | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 356fc4a2b894cbcb226678b4aa320c4590002dbb
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, объект Broker TO Statistics
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Объект производительности SQLServer:Broker TO Statistics сообщает о том, сколько раз в диалогах компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] запрашиваются объекты передачи и как часто объекты передачи записываются в базу данных **tempdb**.  
  
 В объектах передачи записывается состояние передач сообщений для диалога компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Они хранятся в памяти. Чтобы освободить память, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] периодически записывает пакеты неактивных объектов передачи в рабочие таблицы базы данных **tempdb**.  
  
 В следующей таблице перечислены счетчики этого объекта.  
  
|Счетчики объекта SQL Server Broker TO Statistics|Description|  
|----------------------------------------------|-----------------|  
|**Средн. длина пакетов записи**|Среднее число объектов передачи, сохраняемых в пакете.|  
|**Средн. время записи пакета (мс)**|Среднее время в миллисекундах, необходимое для сохранения пакета объектов передачи.|  
|**Средн. время для базовой записи пакета (мс)**|Только для внутреннего применения.|
|**Средн. время между пакетами (мс)**|Среднее время в миллисекундах между записью пакетов объектов передачи.|  
|**Средн. базовое время между пакетами**|Только для внутреннего применения.| 
|**Получено объектов передачи/с**|Число раз в секунду, когда диалоги запрашивали объекты передачи.|  
|**Грязных объектов передачи/с**|Число раз в секунду, когда объекты передачи были отмечены как грязные. Объекты передачи отмечаются как грязные при первом изменении, которое приводит к тому, что копия в памяти отличается от копии в базе данных **tempdb**. Объекты передачи изменяются, когда компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] должен записать изменение в состоянии передач сообщений для диалога.|  
|**Запись объектов передачи/с**|Число раз в секунду, когда пакет объектов передачи был записан в рабочие таблицы базы данных **tempdb** . Большое число записей может говорить о нехватке памяти для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server, объект Access Methods](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [SQL Server, объект Memory Manager](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
