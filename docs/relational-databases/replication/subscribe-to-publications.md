---
title: "Подписка на публикации | Документация Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
caps.latest.revision: "44"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4613a7ee6306ba86b5748377f20c1cf48117815
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="subscribe-to-publications"></a>Подписка на публикации
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Подписка представляет собой запрос на копию данных и объектов из базы данных в публикации. Подписка определяет получаемую публикацию, а также место и время ее получения. При планировании подписок необходимо определить место обработки агентом. Выбранный тип подписки определяет место запуска агента. В случае принудительной подписки агент слияния или агент распространителя запускается у распространителя, а в случае подписки по запросу агент запускается у подписчиков. После того, как подписка создана, ее тип нельзя изменить.  
  
|Подписка|Характеристики|Использовать|  
|------------------|---------------------|--------------|  
|Принудительная подписка|В случае принудительной подписки издатель передает изменения подписчику без запроса со стороны последнего. Изменения могут передаваться подписчикам по запросу, непрерывно или по расписанию. Агент распространителя или агент слияния запускается у распространителя.|Синхронизация данных обычно будет осуществляться непрерывно или по повторяющемуся расписанию.<br /><br /> Для публикаций требуется перемещение данных практически в режиме реального времени.<br /><br /> Повышенная загрузка процессора у распространителя не влияет на производительность.<br /><br /> Наиболее часто используется с репликацией моментальных снимков и с репликацией транзакций.|  
|Подписка по запросу|В случае подписки по запросу подписчик запрашивает изменения, внесенные у издателя. Подписки по запросу позволяют пользователю подписчика определить момент синхронизации изменений данных. Агент распространителя или агент слияния запускается у подписчика.|Синхронизация данных обычно будет осуществляться по запросу или по расписанию, а не непрерывно.<br /><br /> У публикации большое количество подписчиков, и/или запуск всех агентов на распространителе потребует слишком большого количества ресурсов.<br /><br /> Подписчики автономны, не подключены или мобильны. Подписчики будут определять момент подключения и синхронизации изменений.<br /><br /> Наиболее часто используется с репликацией слиянием.|  
  
## <a name="merge-replication-subscription-types"></a>Типы подписки на репликацию слиянием  
 Все типы репликации поддерживают принудительные подписки и подписки по запросу. Для репликации слиянием используются два дополнительных термина с целью различения подписок: клиентские подписки и серверные подписки. Подписки как клиентского, так и серверного типов могут использоваться для принудительных подписок и подписок по запросу. Клиентские подписки подходят для большинства подписчиков, в то время как серверные подписки обычно используются для подписчиков, которые повторно публикуют данные для других подписчиков. Выбор подписки влияет на разрешение конфликтов.  
  
## <a name="non-sql-server-subscribers"></a>Подписчики, отличные от подписчиков SQL Server  
 Клиенты Oracle и IBM DB2 могут подписываться на публикации моментальных снимков и публикации транзакций с использованием принудительных подписок. Дополнительные сведения см. в статье [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
## <a name="creating-subscriptions"></a>Создание подписок  
 Чтобы создать подписку, нужно ввести следующую информацию:  
  
-   Имя публикации.  
  
-   Имя подписчика и базы данных подписки.  
  
-   Где запускается агент распространителя или агент слияния — на распространителе или на подписчике.  
  
-   Агент распространителя или агент слияния работает постоянно, запускается по расписанию или только по запросу.  
  
-   Необходимость создания агентом моментальных снимков исходного моментального снимка для подписки и необходимость применения агентом распространителя или агентом слияния этого моментального снимка на подписчике.  
  
-   Учетные записи, с которыми будет запускаться агент распространителя или агент слияния.  
  
-   Для репликации слиянием — тип подписки: серверная или клиентская.  
  
 **Создание принудительной подписки**  
  
 [Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)  
  
 **Просмотр или изменение свойств принудительной подписки**  
  
 [Просмотр и изменение свойств принудительной подписки](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)  
  
 **Удаление принудительной подписки**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Удаление принудительной подписки](../../relational-databases/replication/delete-a-push-subscription.md)  
  
> [!NOTE]  
>  Удаление подписки не приводит к удалению опубликованных объектов у подписчика.  
  
 **Создание подписки по запросу**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)  
  
 **Просмотр или изменение свойств подписки по запросу**  
  
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  
  
 **Удаление подписки по запросу**  
  
 [Удаление подписки по запросу](../../relational-databases/replication/delete-a-pull-subscription.md)  
  
## <a name="see-also"></a>См. также:  
 [Защита подписчика](../../relational-databases/replication/security/secure-the-subscriber.md)   
 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
