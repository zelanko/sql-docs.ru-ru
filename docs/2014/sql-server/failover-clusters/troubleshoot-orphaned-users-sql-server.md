---
title: Устранение неполадок, связанных с пользователями, утратившими связь с учетной записью (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97bef9ba2298766539d6b852bb41bb89c716c829
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095407"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a>Диагностика пользователей, утративших связь с учетной записью (SQL Server)
  Чтобы войти в экземпляр Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], участник должен иметь допустимое имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это имя используется в процессе проверки подлинности, который проверяет, разрешено ли участнику подключаться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Имена входа на экземпляре сервера, отображаются в **sys.server_principals** представления каталога и **sys.syslogins** Просмотр в режиме совместимости.  
  
 Имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получают доступ к отдельным базам данных с помощью пользователя базы данных, сопоставленного с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Существует два исключения из этого правила:  
  
-   Учетная запись гостя.  
  
     Если в базе данных эта учетная запись включена, она позволяет именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые не сопоставлены с пользователями базы данных, входить в базу данных как пользователь-гость.  
  
-   Членство в группе Microsoft Windows.  
  
     Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , созданное из учетной записи пользователя Windows, может войти в базу данных, если пользователь Windows входит в группу Windows, являющуюся также пользователем базы данных.  
  
 Сведения о сопоставлении имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с пользователем базы данных хранятся в базе данных. Эти сведения включают в себя имя пользователя базы данных и идентификатор безопасности соответствующего имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Разрешения этого пользователя базы данных используются для авторизации в базе данных.  
  
 Пользователь базы данных, соответствующее имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] которого для экземпляра сервера не определено или задано неправильно, не сможет подключиться к этому экземпляру. Такой пользователь называется *утратившим связь с учетной записью* базы данных на этом экземпляре сервера. Пользователь базы данных может утратить связь с учетной записью в случае удаления соответствующего имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, пользователь базы данных может утратить связь с учетной записью после того, как база данных будет восстановлена или прикреплена к другому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Утрата связи с учетной записью может произойти, если пользователь базы данных сопоставлен с идентификатором безопасности, отсутствующим в новом экземпляре сервера.  
  
> [!NOTE]  
>  Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа не может получить доступ к базы данных, в котором он не имеет соответствующего пользователя базы данных пока не **гостевой** включена в этой базе данных. Сведения о создании учетной записи пользователя базы данных см. в разделе [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
## <a name="to-detect-orphaned-users"></a>Обнаружение утративших связь с учетной записью пользователей  
 Чтобы обнаружить пользователей, утративших связь с учетной записью, выполните следующие инструкции языка Transact-SQL:  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 Выходные данные содержат список пользователей и соответствующие идентификаторы безопасности в текущей базе данных, которые не связаны ни с одним именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
> [!NOTE]  
>  **sp_change_users_login** не может использоваться с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имена входа, созданные на основе Windows.  
  
## <a name="to-resolve-an-orphaned-user"></a>Разрешение пользователей, утративших связь с учетной записью  
 Чтобы разрешить пользователя, утратившего связь с учетной записью, используйте следующую процедуру:  
  
1.  Следующая команда повторно связывает учетную запись входа сервера, заданные *< login_name >* с пользователем базы данных с *< пользователь_базы_данных >*.  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     Дополнительные сведения см. в разделе [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
2.  После того как будет выполнен код на предыдущем шаге, пользователь сможет обращаться к базе данных. Пользователь сможет затем изменить пароль *< login_name >* учетной записи входа с помощью **sp_password** хранимой процедуры, как показано ниже:  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  Только имена входа с разрешением ALTER ANY LOGIN могут изменять пароль других имен входа пользователей. Однако только члены роли **sysadmin** могут изменять пароли членов роли **sysadmin** .  
  
    > [!NOTE]  
    >  **sp_password** не может использоваться для [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетных записей Windows. Пользователи, соединяющиеся с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через свою сетевую учетную запись Windows, проходят проверку подлинности в Windows, поэтому их пароли могут быть изменены только в Windows.  
  
     Дополнительные сведения см. в разделе [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)   
 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)   
 [sp_change_users_login (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)   
 [sp_addlogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [Хранимая процедура sp_grantlogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [sp_password (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)   
 [sys.sysusers (Transact-SQL)](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)   
 [sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
