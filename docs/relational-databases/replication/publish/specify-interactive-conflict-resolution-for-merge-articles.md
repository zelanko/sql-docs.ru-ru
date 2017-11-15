---
title: "Настройка интерактивного устранения конфликтов для статей публикации слиянием | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], interactive resolvers
- interactive conflict resolution [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 71733ce639f6797e15d294e811f454f8faf7eb0f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="specify-interactive-conflict-resolution-for-merge-articles"></a>Указание интерактивного устранения конфликтов для статей публикации слиянием
  В данном разделе описывается указание интерактивного устранения конфликтов для статей публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Репликация[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует интерактивный арбитр конфликтов, который позволяет разрешать конфликты вручную при проведении синхронизации по требованию в диспетчере синхронизации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. После того как интерактивное разрешение конфликтов включено, конфликты разрешаются во время синхронизации в интерактивном режиме с помощью интерактивного сопоставителя. Интерактивный сопоставитель доступен через диспетчер синхронизации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Дополнительные сведения см. в статье [Синхронизация подписки с помощью диспетчера синхронизации Windows (диспетчер синхронизации Windows)](../../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для указания интерактивного устранения конфликтов для статей публикации слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Если синхронизация выполнена вне диспетчера синхронизации Windows (по расписанию или по требованию в среде SQL Server Management Studio или мониторе репликации), конфликты разрешаются автоматически без вмешательства пользователя с помощью метода разрешения конфликтов по умолчанию, указанному для статьи. Дополнительные сведения см. в разделе [Interactive Conflict Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-enable-interactive-conflict-resolution-for-an-article"></a>Включение интерактивного разрешения конфликтов для статьи  
  
1.  Выберите таблицу на странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера создания публикаций и доступе к этому диалоговому окну см. в статьях о [создании публикаций](../../../relational-databases/replication/publish/create-a-publication.md) и [просмотре и изменении свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
2.  Щелкните **Свойства статьи**, затем щелкните **Указать свойства выделенной статьи таблицы** или **Указать свойства всех статей таблиц**.  
  
3.  На странице **Свойства статьи — \<Статья>** или **Свойства статьи — \<Тип статьи>** щелкните вкладку **Сопоставитель**.  
  
4.  Выберите **Позволить подписчикам разрешать конфликты в интерактивном режиме во время синхронизации по требованию**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
#### <a name="to-specify-that-a-subscription-should-use-interactive-conflict-resolution"></a>Указание, что подписка должна использовать интерактивное разрешение конфликтов  
  
1.  В диалоговом окне **Свойства подписки — \<подписчик>: \<база данных подписки>** для параметра **Интерактивное разрешение конфликтов** задайте значение **True**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделах [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) и [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно программно указать, чтобы подписчик использовал этот графический интерфейс для разрешения конфликтов статей, если создается подписка по запросу на публикацию слиянием. В интерактивном сопоставителе отображаются только конфликты статей, поддерживающих этот параметр.  
  
#### <a name="to-create-a-merge-pull-subscription-that-uses-the-interactive-resolver"></a>Создание подписки по запросу на публикации слиянием, использующую интерактивный сопоставитель  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав параметр **@publication**. Запомните значение **allow_interactive_resolver** для каждой статьи в результирующем наборе, для которого будет использоваться интерактивный сопоставитель.  
  
    -   Если это значение равно **1**, будет использоваться интерактивный сопоставитель.  
  
    -   Если значение равно **0**, необходимо вначале включить интерактивный сопоставитель для каждой статьи. Для этого выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав параметр **@publication**, **@article**, значение **allow_interactive_resolver** в параметре **@property**и значение **true** в параметре **@value**.  
  
2.  В базе данных подписки на издателе выполните процедуру [sp_addmergepushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md), указав следующие параметры.  
  
    -   **@publisher**, **@publisher_db** (публикуемая база данных) и **@publication**.  
  
    -   Значение **true** в параметре **@enabled_for_syncmgr**.  
  
    -   Значение **true** в параметре **@use_interactive_resolver**.  
  
    -   Сведения учетной записи безопасности, необходимой для агента слияния. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
4.  В базе данных публикации на издателе выполните процедуру [sp_addmergepushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md).  
  
#### <a name="to-define-an-article-that-supports-the-interactive-resolver"></a>Определение статьи, поддерживающей интерактивный сопоставитель  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите имя публикации, которой принадлежит статья, в параметре **@publication**, имя статьи в параметре **@article**, публикуемый объект базы данных в параметре **@source_object**и значение **true** в параметре **@allow_interactive_resolver**. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и разрешение конфликтов данных для публикации слиянием (SQL Server Management Studio)](../../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Interactive Conflict Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
  
