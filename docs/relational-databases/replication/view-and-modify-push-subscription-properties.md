---
title: "Просмотр и изменение свойств принудительной подписки | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "просмотр свойств репликации"
  - "принудительные подписки [репликация SQL Server], свойства"
  - "принудительные подписки [репликация SQL Server], отправка"
  - "принудительные подписки [репликация SQL Server], изменение"
  - "изменение свойств репликации, принудительные подписки"
  - "изменение подписок, среда SQL Server Management Studio"
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Просмотр и изменение свойств принудительной подписки
  В данном разделе описывается просмотр и изменение свойств принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для просмотра и изменения свойств принудительной подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотр и изменение свойств принудительной подписки со стороны издателя:  
  
-    **Свойства подписки — \< издатель>: \< база данных публикации>** диалоговое окно доступно из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   На вкладке **Все подписки** в мониторе репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Просмотр и изменение свойств принудительной подписки в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте соответствующую публикацию, щелкните правой кнопкой мыши подписку и нажмите кнопку **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### Просмотр и изменение свойств принудительной подписки в мониторе репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Принудительные подписки могут быть изменены программно, кроме того, с помощью хранимых процедур репликации можно программно получить доступ к их свойствам. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит подписка.  
  
#### Просмотр свойств принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Укажите параметры **@publication**, **@subscriber**и значение **all** в параметре **@article**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), указав **@subscriber**.  
  
#### Изменение свойств принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changesubscriber](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md), указав **@subscriber** и все параметры для изменения свойств подписчика.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, **@destination_db**, значение **все** для **@article**, как изменяемое свойство подписки **@property**, и новое значение как **@value**. При этом изменятся параметры безопасности для принудительной подписки.  
  
3.  (Необязательно) Чтобы изменить свойства пакета служб DTS подписки, выполните [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md) на подписчике в базе данных подписки. Укажите идентификатор задания агента распространителя в параметре **@jobid** и следующие свойства пакета служб DTS.  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Свойства пакета служб подписки будут изменены.  
  
    > [!NOTE]  
    >  Идентификатор можно получить, выполнив задания [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### Просмотр свойств принудительной подписки на публикацию слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md). Укажите параметры **@publication** и **@subscriber**.  
  
2.  На издателе, хранимую [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), указав **@subscriber**.  
  
#### Изменение свойств принудительной подписки на публикацию слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md). Укажите **@publication**, **@subscriber**, **@subscriber_db**, как изменяемое свойство подписки **@property**, и новое значение как **@value**.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Какие именно классы объектов RMO для этого применяются, зависит от типа публикации этой подписки.  
  
#### Просмотр и изменение свойств принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransSubscription> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, и <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> Свойства.  
  
4.  Задайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> значение свойства.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает значение **false**, то либо на шаге 3 были неверно определены свойства подписки, либо подписка не существует.  
  
6.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.TransSubscription> Свойства, которые можно задать, а затем вызвать <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод.  
  
7.  (Необязательно) Чтобы просмотреть новые параметры, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> метод перезагрузит свойства подписки.  
  
#### Просмотр и изменение свойств принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscription> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, и <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> Свойства.  
  
4.  Задайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> значение свойства.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает значение **false**, то либо на шаге 3 были неверно определены свойства подписки, либо подписка не существует.  
  
6.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.MergeSubscription> Свойства, которые можно задать, а затем вызвать <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод.  
  
7.  (Необязательно) Чтобы просмотреть новые параметры, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> метод перезагрузит свойства подписки.  
  
## См. также:  
 [Просмотр сведений и выполнение задач для подписки и #40; Монитор репликации & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  