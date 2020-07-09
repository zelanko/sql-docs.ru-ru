---
title: Регулятор ввода-вывода XTP в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: fede0215ef21ee7680068629a990ec1a9dd3417f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718956"
---
# <a name="sql-server-xtp-io-governor"></a>Регулятор ввода-вывода XTP в SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
