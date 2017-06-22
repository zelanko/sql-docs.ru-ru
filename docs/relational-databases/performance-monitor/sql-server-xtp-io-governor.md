---
title: "Регулятор ввода-вывода XTP в SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
caps.latest.revision: 2
author: dagiro
ms.author: v-dagir
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dad1b34551ae96587fafdf3f232ce96b33a96846
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-xtp-io-governor"></a>Регулятор ввода-вывода XTP в SQL Server
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Объект производительности регулятора ввода-вывода XTP в SQL Server содержит счетчики, относящиеся к регулятору скорости ввода-вывода для выполняющейся в памяти OLTP.

В следующей таблице описаны счетчики **регулятора ввода-вывода XTP в SQL Server** .

|Счетчик|Description|  
|-------------|-----------------|  
|**Insufficient Credits Waits/sec (Ожиданий при недостаточных кредитах в секунду)**|Число ожиданий из-за недостаточных кредитов в объектах скорости (в секунду).|
|**Io Issued/sec (Выданных операций ввода-вывода/с)**|Количество операций ввода-вывода, выдаваемых в секунду потоками записи на диск.|
|**Log Blocks/sec (Блоков журнала/с)**|Количество блоков журнала, обрабатываемых контроллером в секунду.|
|**Missed Credit Slots (Пропущенные слоты кредитов)**|Число слотов кредитов, пропущенных из-за ожидания кредитов от объекта скорости.|
|**Stale Rate Object Waits/sec (Ожиданий устаревших объектов скорости в секунду)**|Число ожиданий из-за устаревших объектов скорости (в секунду).|
|**Total Rate Objects Published (Всего опубликованных объектов скорости)**|Общее число опубликованных объектов скорости.|
 

## <a name="see-also"></a>См. также:  
[Счетчики производительности XTP (In-Memory OLTP) для SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
