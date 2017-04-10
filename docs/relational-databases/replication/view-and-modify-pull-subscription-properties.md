---
title: "Просмотр и изменение свойств подписки по запросу | Microsoft Docs"
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
  - "изменение подписок"
  - "просмотр свойств репликации"
  - "изменение свойств репликации, подписки по запросу"
  - "подписки по запросу [репликация SQL Server], изменение"
  - "подписки [репликация SQL Server], по запросу"
  - "подписки по запросу [репликация SQL Server], свойства"
  - "изменение подписок, среда SQL Server Management Studio"
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Просмотр и изменение свойств подписки по запросу
  В данном разделе описывается просмотр и изменение свойств подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для просмотра и изменения свойств подписки по запросу используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотр свойств подписки по запросу на издателе или подписчике в **Свойства подписки — \< издатель>: \< база данных публикации>** диалоговое окно доступно из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. На подписчике можно просмотреть и изменить ряд дополнительных свойств. Свойства можно также просмотреть на издателе на вкладке **Все подписки** , доступной в мониторе репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Просмотр свойств подписки по запросу на издателе в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте соответствующую публикацию, щелкните правой кнопкой мыши подписку и нажмите кнопку **Свойства**.  
  
4.  Просмотрите свойства, а затем нажмите кнопку **ОК**.  
  
#### Просмотр и изменение свойств подписки по запросу на подписчике в среде Management Studio  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### Просмотр свойств подписки по запросу на издателе в мониторе репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и нажмите кнопку **Свойства**.  
  
4.  Просмотрите свойства, а затем нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки по запросу можно изменять и получать доступ к их свойствам программно с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит подписка.  
  
#### Просмотр свойств подписки по запросу на публикацию моментальных снимков или публикацию транзакций  
  
1.  На подписчике, выполните [sp_helppullsubscription](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md). Укажите **@publisher**, **@publisher_db**, и **@publication**. Тем самым возвращаются сведения о подписке, хранящиеся в системных таблицах на подписчике.  
  
2.  На подписчике, выполните [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). Укажите **@publisher**, **@publisher_db**, **@publication**, и одно из следующих значений для **@publication_type**:  
  
    -   **0** -принадлежит подписка на публикацию транзакций.  
  
    -   **1** -Подписка принадлежит публикации моментального снимка.  
  
3.  На издателе, хранимую [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md). Укажите параметры **@publication** и **@subscriber**.  
  
4.  На издателе, хранимую [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), указав **@subscriber**. Будут выведены сведения о подписчике.  
  
#### Изменение свойств подписки по запросу на публикацию моментальных снимков или публикацию транзакций  
  
1.  На подписчике, выполните [sp_change_subscription_properties](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), указав **@publisher**, **@publisher_db**, **@publication**, значение **0** (транзакций) или **1** (моментальных снимков) для **@publication_type**, как изменяемое свойство подписки **@property**, и новое значение как **@value**.  
  
2.  (Необязательно) На подписчике в базе данных подписки выполните хранимую процедуру [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md). Укажите идентификатор задания агента распространителя для **@jobid**, и свойства пакета следующий Data Transformation Services (DTS):  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Свойства пакета служб подписки будут изменены.  
  
    > [!NOTE]  
    >  Идентификатор можно получить, выполнив задания [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md).  
  
#### Просмотр свойств подписки по запросу на публикацию слиянием  
  
1.  На подписчике, выполните [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md). Укажите **@publisher**, **@publisher_db**, и **@publication**.  
  
2.  На подписчике, выполните [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md). Укажите **@publisher**, **@publisher_db**, **@publication**, и значение 2 для **@publication_type**.  
  
3.  На издателе, хранимую [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md) для отображения сведений о подписке. Для получения сведений об определенной подписки, необходимо указать **@publication**, **@subscriber**, а значение **запросу** для **@subscription_type**.  
  
4.  На издателе, хранимую [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), указав **@subscriber**. Будут выведены сведения о подписчике.  
  
#### Изменение свойств подписки по запросу на публикацию слиянием  
  
1.  На подписчике, выполните [sp_changemergepullsubscription](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md). Укажите **@publication**, **@publisher**, **@publisher_db**, как изменяемое свойство подписки **@property**, и новое значение как **@value**.  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Конкретные классы объектов RMO, используемые для этого, зависят от типа публикации, для которой создается подписка по запросу.  
  
#### Просмотр или изменение свойств подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPullSubscription> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства подписки, либо подписка не существует.  
  
6.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.TransPullSubscription> Свойства, которые можно задать, а затем вызвать <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод.  
  
7.  (Необязательно) Чтобы просмотреть новые параметры, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> метод, который перезагрузит свойства статьи.  
  
8.  Закройте все соединения.  
  
#### Просмотр или изменение свойств подписки по запросу на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePullSubscription> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства подписки, либо подписка не существует.  
  
6.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.MergePullSubscription> Свойства, которые можно задать, а затем вызвать <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод.  
  
7.  (Необязательно) Чтобы просмотреть новые параметры, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> метод, который перезагрузит свойства статьи.  
  
8.  Закройте все соединения.  
  
## См. также:  
 [Просмотр сведений и выполнение задач для подписки и #40; Монитор репликации & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  