---
title: "Указание интерактивного устранения конфликтов для статей публикации слиянием | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "устранение конфликтов репликации слиянием [репликация SQL Server], интерактивные сопоставители конфликтов"
  - "интерактивное разрешение конфликтов [репликация SQL Server]"
  - "статьи [репликация SQL Server], разрешение конфликтов"
  - "разрешение конфликтов [репликация SQL Server], репликация слиянием"
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Указание интерактивного устранения конфликтов для статей публикации слиянием
  В данном разделе описывается указание интерактивного устранения конфликтов для статей публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Репликация предоставляет интерактивный арбитр конфликтов, который позволяет разрешать конфликты вручную при проведении синхронизации по требованию в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] диспетчера синхронизации Windows. После того как интерактивное разрешение конфликтов включено, конфликты разрешаются во время синхронизации в интерактивном режиме с помощью интерактивного сопоставителя. Интерактивный сопоставитель доступен через диспетчер синхронизации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Дополнительные сведения см. в разделе [синхронизировать подписку с помощью диспетчера синхронизации Windows & #40; Диспетчер синхронизации Windows & #41;](../../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для указания интерактивного устранения конфликтов для статей публикации слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Если синхронизация выполнена вне диспетчера синхронизации Windows (по расписанию или по требованию в среде SQL Server Management Studio или мониторе репликации), конфликты разрешаются автоматически без вмешательства пользователя с помощью метода разрешения конфликтов по умолчанию, указанному для статьи. Дополнительные сведения см. в разделе [Interactive Conflict Resolution](../../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Включение интерактивного разрешения конфликтов для статьи  
  
1.  На **статьи** страница мастера создания публикаций или **Свойства публикации — \< публикация>** диалоговое окно, выберите таблицу. Дополнительные сведения об использовании мастера и о доступе к диалоговому окну см. в разделе [Создать публикацию](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
2.  Щелкните **Свойства статьи**, затем щелкните **Указать свойства выделенной статьи таблицы** или **Указать свойства всех статей таблиц**.  
  
3.  На **Свойства статьи — \< статья>** или **Свойства статьи — \< тип статьи>** щелкните **распознавателя** вкладки.  
  
4.  Выберите **Позволить подписчикам разрешать конфликты в интерактивном режиме во время синхронизации по требованию**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  При работе в **Свойства публикации — \< публикация>** диалоговом нажмите кнопку **ОК** Сохранить и закрыть диалоговое окно.  
  
#### Указание, что подписка должна использовать интерактивное разрешение конфликтов  
  
1.  В **Свойства подписки — \< подписчик>: \< база данных подписки>** диалоговом окне задайте значение **True** для **интерактивное разрешение конфликтов** параметр. Дополнительные сведения о доступе к этому диалоговому окну см. в разделах [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) и [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно программно указать, чтобы подписчик использовал этот графический интерфейс для разрешения конфликтов статей, если создается подписка по запросу на публикацию слиянием. В интерактивном сопоставителе отображаются только конфликты статей, поддерживающих этот параметр.  
  
#### Создание подписки по запросу на публикации слиянием, использующую интерактивный сопоставитель  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав **@publication**. Обратите внимание на значение **allow_interactive_resolver** для каждой статьи в результирующем наборе, для которого будет использоваться интерактивный арбитр конфликтов.  
  
    -   Если это значение равно **1**, будет использоваться интерактивный сопоставитель.  
  
    -   Если значение равно **0**, необходимо вначале включить интерактивный сопоставитель для каждой статьи. Чтобы сделать это, выполните [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав **@publication**, **@article**, значение **allow_interactive_resolver** для **@property**, а значение **true** для **@value**.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md), указав следующие параметры:  
  
    -   **@publisher**, **@publisher_db** (опубликованной базы данных), и **@publication**.  
  
    -   Значение **true** для **@enabled_for_syncmgr**.  
  
    -   Значение **true** для **@use_interactive_resolver**.  
  
    -   Сведения учетной записи безопасности, необходимой для агента слияния. Дополнительные сведения см. в разделе [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md).  
  
#### Определение статьи, поддерживающей интерактивный сопоставитель  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите имя публикации, к которой принадлежит статья, для **@publication**, имя статьи для **@article**, объект базы данных, публикуемые для **@source_object**, а значение **true** для **@allow_interactive_resolver**. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## См. также:  
 [Просмотр и разрешение конфликтов данных для публикаций слиянием & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)   
 [Интерактивное разрешение конфликтов](../../../relational-databases/replication/merge/interactive-conflict-resolution.md)  
  
  