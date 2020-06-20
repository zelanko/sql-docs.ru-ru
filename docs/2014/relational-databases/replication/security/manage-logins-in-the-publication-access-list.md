---
title: Управление именами для входа в списке доступа к публикации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85009908"
---
# <a name="manage-logins-in-the-publication-access-list"></a>Управление именами входа в списке доступа к публикации
  В этом разделе описывается управление именами входа в списке доступа к публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Доступом к публикации управляет список доступа к публикации (PAL). Имена входа и группы можно добавлять в список доступа к публикации и удалять из него.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
-   **Для управления именами входа в списке доступа к публикации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Перед добавлением имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в список доступа к публикации необходимо связать его с пользователем базы данных публикации.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Список доступа к публикации (PAL) можно использовать на странице **список доступа к публикации** диалогового окна **Свойства публикации \<Publication> —** для управления именами входа. Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств публикации](../publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-manage-logins-in-the-pal"></a>Управление именами входа в списке доступа к публикации (PAL)  
  
1.  На странице **список доступа к публикации** диалогового окна **Свойства публикации \<Publication> —** используйте кнопки **Добавить**, **Удалить**и **удалить все** , чтобы добавлять и удалять имена для входа и группы из списка PAL. Не удаляйте учетную запись **distributor_admin** из списка доступа к публикации. Эта учетная запись используется при репликации.  
  
    > [!NOTE]  
    >  Если используется удаленный распространитель, то учетные записи в списке доступа к публикации должны быть доступны как на издателе, так и на распространителе. Это должны быть либо учетные записи домена, либо локальные учетные записи, определенные на обоих серверах. Пароли, связанные с обоими именами входа, должны совпадать.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a>Просмотр групп и имен входа из списка доступа к публикации  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql). В поле ** \@ Публикация**укажите имя публикации. Будут отображены сведения о группах и именах входа из списка доступа к публикации.  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a>Добавление групп и имен входа в список доступа к публикации  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql). Для параметра ** \@ Публикация**укажите имя публикации, а в поле имя ** \@ входа**укажите имя входа или добавляемой группы.  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a>Удаление групп и имен входа из списка доступа к публикации  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql). В поле ** \@ Публикация**укажите имя публикации, а для параметра имя ** \@ входа**укажите имя входа или удаляемой группы.  
  
## <a name="see-also"></a>См. также:  
 [Модель безопасности агента репликации](replication-agent-security-model.md)   
 [Защита топологии репликации](view-and-modify-replication-security-settings.md)   
 [Организация безопасности издателя](secure-the-publisher.md)  
  
  
