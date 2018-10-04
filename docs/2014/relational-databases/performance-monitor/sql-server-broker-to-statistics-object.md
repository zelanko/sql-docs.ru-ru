---
title: SQL Server, объект Broker TO Statistics | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8a9574e4ab6618d08df94e8bd3de3c2b21d6000c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207934"
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, объект Broker TO Statistics
  Объект производительности SQLServer:Broker TO Statistics сообщает о том, сколько раз в диалогах компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] запрашиваются объекты передачи и как часто объекты передачи записываются в базу данных **tempdb**.  
  
 В объектах передачи записывается состояние передач сообщений для диалога компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Они хранятся в памяти. Чтобы освободить память, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] периодически записывает пакеты неактивных объектов передачи в рабочие таблицы базы данных **tempdb**.  
  
 В следующей таблице перечислены счетчики этого объекта.  
  
|Счетчики объекта SQL Server Broker TO Statistics|Описание|  
|----------------------------------------------|-----------------|  
|**Средн. длина пакетов записи**|Среднее число объектов передачи, сохраняемых в пакете.|  
|**Средн. время записи пакета (мс)**|Среднее время в миллисекундах, необходимое для сохранения пакета объектов передачи.|  
|**Средн. время между пакетами (мс)**|Среднее время в миллисекундах между записью пакетов объектов передачи.|  
|**Получено объектов передачи/с**|Число раз в секунду, когда диалоги запрашивали объекты передачи.|  
|**Грязных объектов передачи/с**|Число раз в секунду, когда объекты передачи были отмечены как грязные. Объекты передачи отмечаются как грязные при первом изменении, которое приводит к тому, что копия в памяти отличается от копии в базе данных **tempdb**. Объекты передачи изменяются, когда компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] должен записать изменение в состоянии передач сообщений для диалога.|  
|**Запись объектов передачи/с**|Число раз в секунду, когда пакет объектов передачи был записан в рабочие таблицы базы данных **tempdb** . Большое число записей может говорить о нехватке памяти для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
  
## <a name="see-also"></a>См. также  
 [SQL Server, объект Access Methods](sql-server-access-methods-object.md)   
 [SQL Server, объект Memory Manager](sql-server-memory-manager-object.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](monitor-resource-usage-system-monitor.md)  
  
  
