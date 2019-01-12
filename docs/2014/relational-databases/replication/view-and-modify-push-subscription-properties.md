---
title: Просмотр и изменение свойств принудительной подписки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5dc55cc688f4e40d188492636c3653556f88b1c6
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127264"
---
# <a name="view-and-modify-push-subscription-properties"></a>Просмотр и изменение свойств принудительной подписки
  В данном разделе описывается просмотр и изменение свойств принудительной подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для просмотра и изменения свойств принудительной подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотр и изменение свойств принудительной подписки со стороны издателя:  
  
-   **Свойства подписки — \<издатель >: \<База данных публикации >** диалоговое окно, которое доступно из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   На вкладке **Все подписки** в мониторе репликации. Сведения о запуске монитора репликации см. в [этой статье](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a>Просмотр и изменение свойств принудительной подписки в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте соответствующую публикацию, щелкните правой кнопкой мыши подписку и выберите **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a>Просмотр и изменение свойств принудительной подписки в мониторе репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и выберите **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Принудительные подписки могут быть изменены программно, кроме того, с помощью хранимых процедур репликации можно программно получить доступ к их свойствам. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит подписка.  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Просмотр свойств принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql). Укажите параметры **@publication**, **@subscriber**и значение **all** в параметре **@article**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), указав параметр **@subscriber**.  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Изменение свойств принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql), указав параметр **@subscriber** и любые параметры для свойств подписчика, которые нужно изменить.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql). Укажите параметры **@publication**, **@subscriber**, **@destination_db**, значение **all** в параметре **@article**, изменяемое свойство подписки в параметре **@property**и новое значение в параметре **@value**. При этом изменятся параметры безопасности для принудительной подписки.  
  
3.  Чтобы изменить свойства пакета служб DTS подписки, выполните хранимую процедуру [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) на подписчике для базы данных подписки (необязательно). Укажите идентификатор задания агента распространителя в параметре **@jobid** и следующие свойства пакета служб DTS.  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Свойства пакета служб подписки будут изменены.  
  
    > [!NOTE]  
    >  Идентификатор задания можно получить, выполнив процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a>Просмотр свойств принудительной подписки на публикацию слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql). Укажите параметры **@publication** и **@subscriber**.  
  
2.  Выполните на издателе процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), указав параметр **@subscriber**.  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a>Изменение свойств принудительной подписки на публикацию слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql). Укажите параметры **@publication**, **@subscriber**, **@subscriber_db**, изменяемое свойство подписки в параметре **@property**и новое значение в параметре **@value**.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Какие именно классы объектов RMO для этого применяются, зависит от типа публикации этой подписки.  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>Просмотр и изменение свойств принудительной подписки на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransSubscription> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>и <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> .  
  
4.  Задайте соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> с шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает значение `false`, то либо на шаге 3 были неверно определены свойства подписки, либо подписка не существует.  
  
6.  Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.TransSubscription> , которое можно установить, и затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно).  
  
7.  Чтобы просмотреть новые значения, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> , который выполняет повторную загрузку свойств для подписки (необязательно).  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a>Просмотр и изменение свойств принудительной подписки на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscription> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>и <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> .  
  
4.  Задайте соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> с шага 1 для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает значение `false`, то либо на шаге 3 были неверно определены свойства подписки, либо подписка не существует.  
  
6.  Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.MergeSubscription> , которое можно установить, и затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно).  
  
7.  Чтобы просмотреть новые значения, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> , который выполняет повторную загрузку свойств для подписки (необязательно).  
  
## <a name="see-also"></a>См. также  
 [Просмотр сведений и выполнение задач с помощью монитора репликации](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  
