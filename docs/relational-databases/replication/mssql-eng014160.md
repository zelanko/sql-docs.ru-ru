---
title: "MSSQL_ENG014160 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014160, ошибка"
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014160
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14160|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Задан порог [%s:%s] для публикации [%s]. Срок действия подписки на эту публикацию истек у одного или нескольких подписчиков.|  
  
## Объяснение  
 При репликации можно включить предупреждения для ряда условий. Сюда входит приближение истечения срока действия подписки. Срок действия подписок может закончиться, если они не будут синхронизированы в течение определенного *срока хранения*. Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 При включении предупреждения с помощью монитора репликации или [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), укажите пороговое значение, которое определяет, когда срабатывает предупреждение. При достижении или превышении порогового значения предупреждение отображается в мониторе репликации, а в журнал событий Windows записывается событие. Достижение порогового значения также может приводить к выдаче предупреждения агента SQL Server. Дополнительные сведения см. в разделе [задать пороговые значения и предупреждения в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) и [программно монитор репликации](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## Действие пользователя  
 Решение проблемы зависит от причины выдачи предупреждения:  
  
-   Если превышено пороговое значение, но срок действия подписки еще не истек, синхронизируйте подписку. Дополнительные сведения см. в разделе [синхронизации данных](../../relational-databases/replication/synchronize-data.md).  
  
-   Если агент работал, но неправильно реплицировал изменения, это могло стать причиной истечения срока действия подписки. В случае репликации транзакций удостоверьтесь, что работают агент распространителя и агент чтения журнала. В случае репликации слиянием удостоверьтесь, что работает агент слияния. Сведения о запуске этих агентов см. в разделе [Запуск и остановка агента репликации & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) и [Основные понятия исполняемых файлов агента репликации](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Если срок действия подписки истек, ее необходимо либо повторно инициализировать, либо удалить и создать повторно. Это зависит от типа подписки и того, как давно истек ее срок действия. Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## См. также:  
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  