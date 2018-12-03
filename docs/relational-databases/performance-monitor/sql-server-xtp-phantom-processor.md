---
title: SQL Server XTP Phantom Processor | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ba3422dacac62346012d5631fd036fe6a8a8ed93
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52159142"
---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP Phantom Processor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Объект производительности SQL Server XTP Phantom Processor содержит счетчики, относящиеся к подсистеме обработки фантомов механизма In-Memory OLTP. Этот компонент отвечает за обнаружение фантомных строк в транзакциях, выполняемых на уровне изоляции SERIALIZABLE, а также за контроль соблюдения ограничений в параллельных сценариях.  
  
 В этой таблице описываются счетчики объекта **SQL Server XTP Phantom Processor** .  
  
|Счетчик|Описание|  
|-------------|-----------------|  
|**Число попыток сканирования «пыльных углов»/с (от Phantom)**|Число повторных попыток сканирования из-за конфликтов записи при обработке «пыльных углов», выданное Phantom Processor (в среднем), в секунду Это счетчик очень низкого уровня, не предназначенный для пользователей.|  
|**Удалено истекших фантомных строк/с**|Число просроченных строк, удаленных фантомными сканированиями (в среднем), в секунду.|  
|**Количество затронутых фантомных просроченных строк/с**|Число просроченных строк, затронутых фантомными сканированиями (в среднем), в секунду.|  
|**Количество затронутых фантомных строк с истекающим сроком действия /с**|Число строк с истекающим сроком действия, затронутых фантомными сканированиями (в среднем), в секунду.|  
|**Затронутых фантомных строк/с**|Число строк, затронутых фантомными сканированиями (в среднем), в секунду.|  
|**Запущено фантомных сканирований/с**|Число начатых фантомных сканирований (в среднем), в секунду.|  
  
## <a name="see-also"></a>См. также:  
 [Счетчики производительности XTP (In-Memory OLTP) для SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
