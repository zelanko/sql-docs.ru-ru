---
title: "MSSQL_ENG014162 | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014162 error
ms.assetid: a15eef3f-219f-45d3-8286-6a864c85a723
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 49b9725c20bc7cf985c760cd7457d30b72afbe5c
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng014162"></a>MSSQL_ENG014162
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14162|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Убедитесь в том, что агент слияния запущен и соответствует предъявляемому требованию.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит превышение определенного промежутка времени, необходимого для синхронизации изменений между издателем и подписчиком слияния. Для соединений по локальной сети и коммутируемых соединений можно указать разные значения времени.  
  
 Когда предупреждение включается при помощи монитора репликации или процедуры [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), необходимо указать пороговое значение, определяющее, в какой момент выдается предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в статьях [Настройка пороговых значений и предупреждений в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). и [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Если подписка превышает пороговое значение промежутка времени, необходимо определить, является ли это проблемой производительности системы или свидетельствует о необходимости изменить пороговое значение. После настройки репликации разработайте базовый уровень производительности, позволяющий определить работу репликации при рабочей нагрузке, типичной для ваших приложений и топологии. Включите в базовый уровень продолжительность синхронизации, чтобы правильно выбрать подходящее пороговое значение.  
  
 Если пороговое значение выбрано верно, но превышение порогового значения все же наблюдается, то нужно определить, где в системе находится узкое место по производительности. Дополнительные сведения о мониторинге и устранении неполадок, влияющих на производительность репликации, см. в следующих разделах:  
  
-   [Наблюдение за производительностью с помощью монитора репликации](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) (в частности, раздел "Просмотр подробных сведений о производительности синхронизации для репликации слиянием").  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
