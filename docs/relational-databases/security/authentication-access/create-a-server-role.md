---
title: "Создание роли сервера | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.SWB.SERVERROLE.GENERAL.F1
- sql13.swb.serverrole.memberships.f1
- sql13.swb.serverrole.members.f1
helpviewer_keywords: SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 9d8091e17c7272e0979afa979f2f5e995ca714e0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-server-role"></a>Создание роли сервера
  В этом разделе описывается создание новой роли сервера в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание новой роли сервера с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Ролям сервера нельзя предоставить разрешение на защищаемые объекты уровня базы данных. Сведения о создании ролей базы данных см. в статье [CREATE ROLE (Transact-SQL)](../../../t-sql/statements/create-role-transact-sql.md).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
  
-   Требует разрешения CREATE SERVER ROLE или членства в предопределенной роли сервера.  
  
-   Также требует разрешения IMPERSONATE на *server_principal* для имен входа, разрешения ALTER для ролей сервера, которые используются в качестве *server_principal*, или членства в группе Windows, которая используется в качестве server_principal.  
  
-   Если для назначения владельца роли сервера указывается параметр AUTHORIZATION, необходимы также следующие разрешения.  
  
    -   Для передачи роли сервера во владение другому имени входа необходимо связанное с этим именем входа разрешение IMPERSONATE.  
  
    -   Для передачи роли сервера во владение другой роли сервера необходимо членство в роли сервера-получателя или связанное с этой ролью сервера разрешение ALTER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-new-server-role"></a>Создание новой роли сервера  
  
1.  В обозревателе объектов разверните сервер, на котором необходимо создать новую роль сервера.  
  
2.  Разверните папку **Безопасность** .  
  
3.  Щелкните правой кнопкой мыши папку **Роли сервера** и выберите **Создать роль сервера…**  
  
4.  В диалоговом окне **Новая роль сервера —***server_role_name* на странице **Общие** введите имя новой роли сервера в поле **Имя роли сервера** .  
  
5.  В поле **Владелец** введите имя участника на уровне сервера, которому будет принадлежать новая роль. Также можно нажать кнопку с многоточием **(...)** , чтобы открыть диалоговое окно **Выбор имени входа или роли сервера** .  
  
6.  В поле **Защищаемые объекты**выберите один или несколько защищаемых объектов уровня сервера. Когда выбран защищаемый объект, роли сервера могут быть предоставлены или запрещены разрешения для этого объекта.  
  
7.  В поле **Разрешения: явный** установите флажок, чтобы предоставить, предоставить с правом передачи или отменить разрешение для этой роли сервера на выделенные защищаемые объекты. Если разрешение не может быть предоставлено или отменено для всех выделенных защищаемых объектов, разрешение представляется как частично выбранное.  
  
8.  На странице **Члены** с помощью кнопки **Добавить** добавьте имена входа, представляющие определенных пользователей или их группы, в новую роль сервера.  
  
9. Определяемая пользователем роль сервера может быть членом другой роли сервера. На странице **Членство** установите флажок, чтобы текущая, определяемая пользователем роль сервера стала членом выбранной роли сервера.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-new-server-role"></a>Создание новой роли сервера  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [CREATE SERVER ROLE (Transact-SQL)](../../../t-sql/statements/create-server-role-transact-sql.md).  
  
  
