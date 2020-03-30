---
title: SQL Server, объект Batch Resp Statistics | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Batch Resp Statistics
ms.assetid: a58e8733-6a8d-4b47-b5cb-042e813d808a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 87045f104bdf183c91c3b60b0d85c4a64929359e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67987193"
---
# <a name="sql-server-batch-resp-statistics-object"></a>SQL Server, объект статистики по ответам пакетов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Объект производительности **SQLServer:Batch Resp Statistics** предоставляет счетчики для отслеживания времени ответа пакета SQL Server.

В следующей таблице представлены объекты производительности **Batch Resp Statistics** SQL Server.


|**Счетчики Batch Resp Statistics SQL Server**|Description|  
|-------------|-----------------|  
|**Batches >=000000ms & \<000001ms**|Количество пакетов SQL, у которых время ответа больше или равно 0 мс, но меньше 1 мс.|
|**Batches >=000001ms & \<000002ms**|Количество пакетов SQL, у которых время ответа больше или равно 1 мс, но меньше 2 мс.|
|**Batches >=000002ms & \<000005ms**|Количество пакетов SQL, у которых время ответа больше или равно 2 мс, но меньше 5 мс.|
|**Batches >=000005ms & \<000010ms**|Количество пакетов SQL, у которых время ответа больше или равно 5 мс, но меньше 10 мс.|
|**Batches >=000010ms & \<000020ms**|Количество пакетов SQL, у которых время ответа больше или равно 10 мс, но меньше 20 мс.|
|**Batches >=000020ms & \<000050ms**|Количество пакетов SQL, у которых время ответа больше или равно 20 мс, но меньше 50 мс.|
|**Batches >=000050ms & \<000100ms**|Количество пакетов SQL, у которых время ответа больше или равно 50 мс, но меньше 100 мс.|
|**Batches >=000100ms & \<000200ms**|Количество пакетов SQL, у которых время ответа больше или равно 100 мс, но меньше 200 мс.|
|**Batches >=000200ms & \<000500ms**|Количество пакетов SQL, у которых время ответа больше или равно 200 мс, но меньше 500 мс.|
|**Batches >=000500ms & \<001000ms**|Количество пакетов SQL, у которых время ответа больше или равно 500 мс, но меньше 1000 мс.|
|**Batches >=001000ms & \<002000ms**|Количество пакетов SQL, у которых время ответа больше или равно 1000 мс, но меньше 2000 мс|
|**Batches >=002000ms & \<005000ms**|Количество пакетов SQL, у которых время ответа больше или равно 2000 мс, но меньше 5000 мс.|
|**Batches >=005000ms & \<010000ms**|Количество пакетов SQL, у которых время ответа больше или равно 5000 мс, но меньше 10000 мс.|
|**Batches >=010000ms & \<020000ms**|Количество пакетов SQL, у которых время ответа больше или равно 10000 мс, но меньше 20000 мс.|
|**Batches >=020000ms & \<050000ms**|Количество пакетов SQL, у которых время ответа больше или равно 20000 мс, но меньше 50000 мс.|
|**Batches >=050000ms & \<100000ms**|Количество пакетов SQL, у которых время ответа больше или равно 50000 мс, но меньше 100000 мс.| 
|**Пакетов >=100000 мс**|Количество пакетов SQL, у которых время ответа больше или равно 100000 мс.| 

Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Элемент|Description|  
|----------|-----------------|  
|**CPU Time:Requests**|Время, затраченное ЦП на запрос.|  
|**CPU Time:Total(ms)**|Общее время, затраченное ЦП на пакет.|  
|**Elapsed Time:Requests**|Затраченное время для запроса.|  
|**Elapsed Time:Total(ms)**|Затраченное время для пакета.|  

## <a name="see-also"></a>См. также:
[SQL Server, объект Plan Cache](../../relational-databases/performance-monitor/sql-server-plan-cache-object.md)  
[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
