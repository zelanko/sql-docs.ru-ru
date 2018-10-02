---
title: Регулятор ввода-вывода XTP в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: e5426fcba665e799f64b3e139da4650b5068507e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642269"
---
# <a name="sql-server-xtp-io-governor"></a>Регулятор ввода-вывода XTP в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Объект производительности регулятора ввода-вывода XTP в SQL Server содержит счетчики, относящиеся к регулятору скорости ввода-вывода для выполняющейся в памяти OLTP.

В следующей таблице описаны счетчики **регулятора ввода-вывода XTP в SQL Server** .

|Счетчик|Описание|  
|-------------|-----------------|  
|**Insufficient Credits Waits/sec (Ожиданий при недостаточных кредитах в секунду)**|Число ожиданий из-за недостаточных кредитов в объектах скорости (в секунду).|
|**Io Issued/sec (Выданных операций ввода-вывода/с)**|Количество операций ввода-вывода, выдаваемых в секунду потоками записи на диск.|
|**Log Blocks/sec (Блоков журнала/с)**|Количество блоков журнала, обрабатываемых контроллером в секунду.|
|**Missed Credit Slots (Пропущенные слоты кредитов)**|Число слотов кредитов, пропущенных из-за ожидания кредитов от объекта скорости.|
|**Stale Rate Object Waits/sec (Ожиданий устаревших объектов скорости в секунду)**|Число ожиданий из-за устаревших объектов скорости (в секунду).|
|**Total Rate Objects Published (Всего опубликованных объектов скорости)**|Общее число опубликованных объектов скорости.|
 

## <a name="see-also"></a>См. также:  
[Счетчики производительности XTP (In-Memory OLTP) для SQL Server](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
