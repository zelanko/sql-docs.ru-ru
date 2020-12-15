---
title: Масштабируемые группы PolyBase | Документация Майкрософт
description: Используйте функцию группы PolyBase для создания кластера экземпляров SQL Server. Повышает производительность запросов для больших наборов данных из внешних источников.
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
f1_keywords:
- sql13.swb.polybasescaleoutcluster.page.f1
helpviewer_keywords:
- PolyBase
- PolyBase, scale-out groups
- scale-out PolyBase
ms.assetid: c7810135-4d63-4161-93ab-0e75e9d10ab5
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>= sql-server-2016'
ms.openlocfilehash: 3928d00a2b72c4d1484fa8b30ca579a5af0ef34c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97416345"
---
# <a name="polybase-scale-out-groups"></a>Масштабируемые группы PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Обработка больших наборов данных в Hadoop или хранилище BLOB-объектов Azure автономным экземпляром SQL Server с PolyBase может сопровождаться снижением производительности. Группы PolyBase позволяют создавать кластеры экземпляров SQL Server для обработки больших наборов данных из внешних источников данных (например, Hadoop или хранилища BLOB-объектов Azure), используя возможности масштабирования. Это помогает повысить производительность запросов. Теперь можно масштабировать вычисления SQL Server в соответствии с требованиями производительности рабочей нагрузки. Масштабируемая группа PolyBase — это группа экземпляров SQL Server, позволяющая обрабатывать большие наборы внешних данных в архитектуре параллельной обработки. Производительность загрузки данных и запросов может увеличиваться линейно по мере добавления дополнительных экземпляров SQL Server в группу. 
  
См. разделы [Приступая к работе с PolyBase](./polybase-guide.md) и [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md).
  
![Схема групп горизонтального увеличения масштаба PolyBase.](../../relational-databases/polybase/media/polybase-scale-out-groups.png "Масштабируемые группы PolyBase")  
  
## <a name="head-node"></a>Головной узел  

Головной узел содержит экземпляр SQL Server, на который отправляются запросы PolyBase. Каждая группа PolyBase может иметь только один головной узел. Головной узел — это логическая группа на экземпляре SQL Server, в которую входят ядро СУБД SQL Server, а также ядро PolyBase и служба "Перемещение данных PolyBase". Для головного узла с SQL Server 2017 и SQL Server 2016 должен использоваться выпуск Enterprise. Начиная с SQL Server 2019, для головного узла PolyBase можно использовать выпуск Enterprise либо Standard.
  
## <a name="compute-node"></a>Вычислительный узел

Вычислительный узел содержит экземпляр SQL Server, который помогает выполнять масштабируемую обработку запросов к внешним данным. Вычислительный узел — это логическая группа на экземпляре SQL Server, в которую входят SQL Server и служба перемещения данных PolyBase. Группа PolyBase может включать несколько вычислительных узлов. В головном узле и вычислительных узлах должна использоваться одна и та же версия SQL Server. В первом выпуске SQL Server 2016 допускалось, чтобы для вычислительных узлов использовались выпуски Enterprise или Standard. Начиная с SQL Server 2016 с пакетом обновления 1 (SP1), для вычислительный узлов могут использоваться все выпуски SQL Server.

## <a name="scale-out-reads"></a>Масштабируемое чтение

Секционированные таблицы выиграют от использования масштабируемого чтения при запросах к внешним экземплярам SQL Server, Oracle или Teradata. Каждый узел в масштабируемой группе PolyBase может запустить до 8 средств для чтения внешних данных. И каждому средству чтения назначается один раздел во внешней таблице. 

Предположим, что у вас есть внешняя таблица SQL Server с 12 секциями (за каждый месяц) и масштабируемая группа PolyBase с 3 узлами. Каждый узел будет использовать по 4 средства чтения PolyBase для обработки каждой из 12 секций. Это продемонстрировано на следующей картинке. 

> [!NOTE]
>  Процесс отличается от масштабируемого чтения в Hadoop. 

![Масштабируемое чтение в PolyBase](../../relational-databases/polybase/media/polybase-scale-out-groups2.png "Масштабируемые группы PolyBase")
  
## <a name="distributed-query-processing"></a>Распределенная обработка запросов  

Запросы PolyBase отправляются на SQL Server на головном узле. Часть запроса, которая относится к внешним таблицам, передается в ядро PolyBase.
  
Ядро PolyBase — это ключевой компонент в процессе обработки запросов PolyBase. Оно анализирует запрос к внешним данным, создает план запроса и распределяет работу между службами перемещения данных на вычислительных узлах. После выполнения этой работы ядро PolyBase получает результаты от вычислительных узлов и отправляет их на SQL Server для финальной обработки и передачи клиенту.
  
Служба перемещения данных PolyBase получает инструкции от ядра PolyBase и передает данные между HDFS и SQL Server, а также между экземплярами SQL Server на головном и вычислительных узлах.
  
## <a name="next-steps"></a>Дальнейшие действия

Чтобы настроить масштабируемую группу PolyBase, обратитесь к следующему руководству:

[Улучшение масштабируемых групп PolyBase в Windows](configure-scale-out-groups-windows.md)

## <a name="see-also"></a>См. также:

 [sys-dm-exec-compute-nodes](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)   
 [sys-dm-exec-compute-node-status](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-status-transact-sql.md)   
 [sys.dm_exec_compute_node_errors](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md)
