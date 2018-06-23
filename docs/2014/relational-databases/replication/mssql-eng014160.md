---
title: MSSQL_ENG014160 | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0315073cad8a76dea71d3bfce47ad7ebaab0d196
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101052"
---
# <a name="mssqleng014160"></a>MSSQL_ENG014160
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14160|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Срок действия подписки на эту публикацию истек у одного или нескольких подписчиков.|  
  
## <a name="explanation"></a>Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит приближение истечения срока действия подписки. Срок действия подписок может закончиться, если они не будут синхронизированы в течение определенного *срока хранения*. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 Когда предупреждение включается при помощи монитора репликации или процедуры [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), необходимо указать пороговое значение, определяющее, в какой момент выдается предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в статьях [Настройка пороговых значений и предупреждений в мониторе репликации](monitor/set-thresholds-and-warnings-in-replication-monitor.md). и [Наблюдение за репликацией программным образом](monitor/monitoring-replication-overview.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Решение проблемы зависит от причины выдачи предупреждения:  
  
-   Если превышено пороговое значение, но срок действия подписки еще не истек, синхронизируйте подписку. Дополнительные сведения см. в разделе [Синхронизация данных](synchronize-data.md).  
  
-   Если агент работал, но неправильно реплицировал изменения, это могло стать причиной истечения срока действия подписки. В случае репликации транзакций удостоверьтесь, что работают агент распространителя и агент чтения журнала. В случае репликации слиянием удостоверьтесь, что работает агент слияния. Дополнительные сведения о запуске этих агентов см. в статьях [Запуск и остановка агента репликации (среда SQL Server Management Studio)](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](concepts/replication-agent-executables-concepts.md).  
  
-   Если срок действия подписки истек, ее необходимо либо повторно инициализировать, либо удалить и создать повторно. Это зависит от типа подписки и того, как давно истек ее срок действия. Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
