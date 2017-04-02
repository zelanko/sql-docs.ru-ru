---
title: "Субъекты (компонент Database Engine) | Microsoft Docs"
ms.custom: ""
ms.date: "01/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.roleproperties.selectroll.f1"
  - "sql13.swb.databaseuser.permissions.user.f1--May use common.permissions"
helpviewer_keywords: 
  - "сертификаты [SQL Server], субъекты"
  - "роли [SQL Server], субъекты"
  - "разрешения [SQL Server], субъекты"
  - "##MS_SQLAuthenticatorCertificate##"
  - "субъекты [SQL Server]"
  - "##MS_SQLResourceSigningCertificate##"
  - "группы [SQL Server], субъекты"
  - "##MS_AgentSigningCertificate##"
  - "проверка подлинности [SQL Server], субъекты"
  - "схемы [SQL Server], субъекты"
  - "субъекты [SQL Server], о субъектах"
  - "безопасность [SQL Server], субъекты"
  - "пользователи [SQL Server], субъекты"
  - "##MS_SQLReplicationSigningCertificate##"
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
caps.latest.revision: 57
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# Субъекты (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  *Субъекты* — это сущности, которые могут запрашивать ресурсы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Как и другие компоненты модели авторизации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], участников можно иерархически упорядочить. Область влияния субъекта зависит от его области определения (Windows, сервер, база данных) и того, неделимый это субъект или коллективный. Имя входа Windows является примером индивидуального (неделимого) субъекта, а группа Windows — коллективного. Каждый субъект имеет идентификатор безопасности (SID).  
  
 **Субъекты уровня Windows**  
  
-   Имя входа домена Windows  
  
-   Локальное имя входа Windows  
  
 **Субъекты**-**уровня** **SQL Server**  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Имя входа  
  
-   Роль сервера  
  
 **Субъекты уровня базы данных**  
  
-   Пользователь базы данных  
  
-   Роль базы данных  
  
-   Роль приложения  
  
## Имя входа «sa» SQL Server  
 Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa является субъектом уровня сервера. По умолчанию оно создается при установке экземпляра. Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] базой данных для имени входа sa по умолчанию является master. Это поведение было изменено по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## Роль базы данных public  
 Каждый пользователь базы данных является членом роли базы данных public. Если пользователю не были предоставлены или запрещены особые разрешения на доступ к защищаемому объекту, то он наследует для него разрешения роли public.  
  
## INFORMATION_SCHEMA и sys  
 Каждая база данных включает в себя две сущности, которые отображены в качестве пользователей в представлениях каталога: INFORMATION_SCHEMA и sys. Они необходимы для работы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; эти пользователи не являются субъектами и не могут быть изменены или удалены.  
  
## Имена входа SQL Server на основе сертификата  
 Субъекты уровня сервера, имеющие имена, заключенные в хэш-символы (##), — только для внутреннего системного пользования. Следующие участники создаются из сертификатов при установке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и не должны удаляться.  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## Пользователь-гость  
 Каждая база данных включает в себя пользователя **guest**. Разрешения, предоставленные пользователю **guest**, наследуются пользователями, которые имеют доступ к базе данных, но не обладают учетной записью пользователя в ней. Пользователя **guest** нельзя удалить, но его можно отключить, если отменить его разрешение **CONNECT**. Разрешение **CONNECT** можно отменить, выполнив инструкцию `REVOKE CONNECT FROM GUEST` в любой базе данных, кроме master или tempdb.  
  
## Клиент и сервер базы данных  
 По определению клиент и сервер базы данных являются защищаемыми субъектами безопасности. Данные сущности могут пройти взаимную проверку подлинности перед установкой безопасного сетевого соединения. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает протокол проверки подлинности [Kerberos](http://go.microsoft.com/fwlink/?LinkId=100758), который определяет, как клиенты взаимодействуют со службой проверки подлинности в сети.  
  
## Связанные задачи  
 Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
 Данный раздел электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] содержит следующие подразделы.  
  
-   [Инструкции по управлению именами входа, пользователями и схемами](../../../relational-databases/security/authentication-access/managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [Роли уровня сервера](../../../relational-databases/security/authentication-access/server-level-roles.md)  
  
-   [Роли уровня базы данных](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
-   [Роли приложений](../../../relational-databases/security/authentication-access/application-roles.md)  
  
## См. также:  
 [Обеспечение безопасности SQL Server](../../../relational-databases/security/securing-sql-server.md)   
 [sys.database_principals (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.sql_logins (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [Роли уровня сервера](../../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Роли уровня базы данных](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  