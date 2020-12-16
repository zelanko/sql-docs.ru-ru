---
description: MSSQL_ENG014161
title: MSSQL_ENG014161 | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 4a0549c07e81188955edb2a255f50dda26f8acbe
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97432419"
---
# <a name="mssql_eng014161"></a>MSSQL_ENG014161
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14161|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Убедитесь, что агент чтения журналов и агент распространителя запущены и соответствуют требованию по задержке.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит превышение определенного значения задержки для подписок на публикацию транзакций. Задержка — это интервал времени между фиксацией транзакции на издателе и фиксацией соответствующей транзакции на подписчике.  
  
 Когда предупреждение включается при помощи монитора репликации или процедуры [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), необходимо указать пороговое значение, определяющее, в какой момент выдается предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в статьях [Настройка пороговых значений и предупреждений в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). и [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Если подписка превышает пороговое значение задержки, необходимо определить, является это проблемой производительности системы или свидетельствует о необходимости скорректировать пороговое значение. После настройки репликации разработайте базовый уровень производительности, позволяющий определить работу репликации при рабочей нагрузке, типичной для ваших приложений и топологии. Включите в базовый уровень задержку, чтобы правильно выбрать подходящее пороговое значение.  
  
 Если пороговое значение выбрано верно, но превышение порогового значения все же наблюдается, то нужно определить, где в системе находится узкое место по производительности. Дополнительные сведения о мониторинге и устранении неполадок, влияющих на производительность репликации, см. в следующих разделах:  
  
-   [Измерение задержки и проверка правильности соединений для репликации транзакций](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [Наблюдение за производительностью с помощью монитора репликации](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
