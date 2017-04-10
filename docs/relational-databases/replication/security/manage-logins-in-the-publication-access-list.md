---
title: "Управление именами входа в списке доступа к публикации | Microsoft Docs"
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
  - "имена входа [репликация SQL Server], список доступа к публикации"
  - "публикации [репликация SQL Server], списки доступа к публикации"
  - "список доступа к публикации (PAL)"
  - "PAL (список доступа к публикации)"
  - "имена входа [репликация SQL Server], управление"
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Управление именами входа в списке доступа к публикации
  В этом разделе описывается управление именами входа в списке доступа к публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Доступом к публикации управляет список доступа к публикации (PAL). Имена входа и группы можно добавлять в список доступа к публикации и удалять из него.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
-   **Для управления именами входа в списке доступа к публикации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Перед добавлением имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в список доступа к публикации необходимо связать его с пользователем базы данных публикации.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Использовать список доступа к публикации (PAL) на **список доступа к публикации** Страница **Свойства публикации — \< публикация>** диалоговое окно Управление именами входа. Дополнительные сведения о том, как получить доступ к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Управление именами входа в списке доступа к публикации (PAL)  
  
1.  На **список доступа к публикации** Страница **Свойства публикации — \< публикация>** диалоговом **Добавить**, **Удалить**, и **Удалить все** кнопки для добавления и удаления имен входа и групп из списка доступа к публикации. Не удаляйте **distributor_admin** из списка доступа к публикации. Эта учетная запись используется при репликации.  
  
    > [!NOTE]  
    >  Если используется удаленный распространитель, то учетные записи в списке доступа к публикации должны быть доступны как на издателе, так и на распространителе. Это должны быть либо учетные записи домена, либо локальные учетные записи, определенные на обоих серверах. Пароли, связанные с обоими именами входа, должны совпадать.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Просмотр групп и имен входа из списка доступа к публикации  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_help_publication_access](../../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md). Для параметра **@publication**укажите имя публикации. Будут отображены сведения о группах и именах входа из списка доступа к публикации.  
  
#### Добавление групп и имен входа в список доступа к публикации  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_grant_publication_access](../../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md). Для параметра **@publication**укажите имя публикации, а в параметре **@login**— имя входа или имя группы, которое нужно добавить.  
  
#### Удаление групп и имен входа из списка доступа к публикации  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_revoke_publication_access](../../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md). Для параметра **@publication**укажите имя публикации, а в параметре **@login**укажите имя входа или имя группы, которое нужно удалить.  
  
## См. также:  
 [Управление именами входа в списке доступа к публикации](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)   
 [Модель безопасности агента репликации](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Организация безопасности топологии репликации](../../../relational-databases/replication/security/secure-a-replication-topology.md)   
 [Организация безопасности издателя](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  