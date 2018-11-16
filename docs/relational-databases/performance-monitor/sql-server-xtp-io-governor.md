---
title: Регулятор ввода-вывода XTP в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 34ceefa87a51ff0bc0c22643e18c8fb0e2393ace
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558311"
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
