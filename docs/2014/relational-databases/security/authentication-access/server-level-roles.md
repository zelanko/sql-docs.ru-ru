---
title: Роли уровня сервера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.Security.BUILTIN.administrators
- sql12.Security.NT_AUTHORITY.SYSTEM
helpviewer_keywords:
- roles [SQL Server], server-level
- principals [SQL Server], server-level
- CONTROL SERVER permission
- fixed server roles [SQL Server]
- credentials [SQL Server], roles
- sysadmin fixed server role
- server-level roles [SQL Server]
- authentication [SQL Server], roles
ms.assetid: 7adf2ad7-015d-4cbe-9e29-abaefd779008
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 95ffdd52ff4c71039a87f177e67d51cb81830c68
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531856"
---
# <a name="server-level-roles"></a>Роли уровня сервера
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет роли уровня сервера и помогает управлять разрешениями на сервере. Эти роли являются субъектами безопасности, группирующими других участников. Разрешения ролей уровня сервера распространяются на весь сервер. (*Роли* похожи на *группы* в операционной системе Windows.)  
  
 Предопределенные роли сервера предусмотрены для удобства и обратной совместимости. Задавайте больше специфических прав каждый раз, когда это возможно.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет девять предопределенных ролей сервера. Разрешения, назначенные предопределенным ролям сервера, не могут быть изменены. Начиная с [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], можно создавать пользовательские роли сервера и добавлять разрешения на уровне сервера таким пользовательским ролям.  
  
 В роли уровня сервера можно добавлять субъекты уровня сервера (имена входа, учетные записи Windows и группы Windows[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ). Каждый член предопределенной роли сервера может добавлять другие имена входа к той же роли. Члены пользовательских ролей сервера не могут добавлять других участников на уровне сервера в роль.  
  
## <a name="fixed-server-level-roles"></a>Предопределенные роли уровня сервера  
 В следующей таблице представлены предопределенные роли уровня сервера и их возможности.  
  
|Предопределенная роль уровня сервера|Описание|  
|------------------------------|-----------------|  
|sysadmin|Члены предопределенной роли сервера sysadmin могут выполнять любые действия на сервере.|  
|serveradmin|Члены предопределенной роли сервера serveradmin могут изменять параметры конфигурации на уровне сервера, а также выключать сервер.|  
|securityadmin|Элементы предопределенной роли сервера securityadmin управляют именами входа и их свойствами. Они могут предоставлять, запрещать и отменять разрешения на уровне сервера (инструкции GRANT, DENY и REVOKE). Они также могут предоставлять, запрещать и отменять разрешения на уровне базы данных (инструкции GRANT, DENY и REVOKE) при наличии доступа к базе данных. Кроме того, они могут сбрасывать пароли для имен входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> **\*\* Примечание по безопасности. \*\*** Возможность предоставления доступа к компоненту [!INCLUDE[ssDE](../../../includes/ssde-md.md)] и настройки разрешений пользователей позволяют администратору безопасности назначать большинство разрешений сервера. `securityadmin` Роли должны рассматриваться как эквивалент `sysadmin` роли.|  
|processadmin|Члены предопределенной роли сервера processadmin могут завершать процессы, работающие на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|setupadmin|Члены предопределенной роли сервера setupadmin могут добавлять или удалять связанные серверы с помощью инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)] . (Членство в роли sysadmin необходимо при использовании службы [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)|  
|bulkadmin|Члены предопределенной роли сервера bulkadmin могут выполнять инструкцию BULK INSERT.|  
|diskadmin|Предопределенная роль сервера diskadmin используется для управления файлами на диске.|  
|dbcreator|Члены предопределенной роли сервера dbcreator могут создавать, изменять, удалять и восстанавливать любые базы данных.|  
|public|Каждое имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] принадлежит к роли сервера public. Если для участника на уровне сервера не были предоставлены или запрещены конкретные разрешения на защищаемый объект, он наследует разрешения роли public на этот объект. Разрешения роли public следует назначать только тому объекту, который будет доступен всем пользователям. Нельзя изменить членство в роли public.<br /><br /> Примечание. Роль public реализована не так, как другие роли. Однако разрешения для роли public можно назначать, отменять или отзывать.|  
  
## <a name="permissions-of-fixed-server-roles"></a>Разрешения Предопределенных Ролей Сервера  
 Каждая предопределенная роль сервера обладает определенными разрешениями, назначенными ей. Список разрешений, назначенных ролям сервера, доступен в [Предопределенные Роли Сервера Ядра СУБД и Предопределенные Роли Базы Данных](https://social.technet.microsoft.com/wiki/contents/articles/2024.database-engine-fixed-server-and-fixed-database-roles.aspx).  
  
> [!IMPORTANT]  
>  Разрешение `CONTROL SERVER` похоже на, но не идентично `sysadmin` предопределенной роли сервера. Разрешения не влекут за собой членства роли, а членства роли не предоставляют разрешений. (Пример `CONTROL SERVER` не подразумевает членство в `sysadmin` предопределенной роли сервера.) Однако иногда возможно олицетворять между ролями и эквивалентными разрешениями. Большинство команд `DBCC` и многие системные процедуры требуют членство в `sysadmin` предопределенной роли сервера. Список из 171 системных хранимых процедур, которые требуют `sysadmin` членства, см. в блоге-Посте Андреаса Вольтера [УПРАВЛЕНИЕ СЕРВЕРОМ против sysadmin/sa: разрешения, системные процедуры, DBCC, автоматическое создание схем и прав доступа предостережения эскалации -](http://www.insidesql.org/blogs/andreaswolter/2013/08/control-server-vs-sysadmin-sa-permissions-privilege-escalation-caveats).  
  
## <a name="server-level-permissions"></a>Разрешение на уровне сервера  
 В пользовательские роли сервера можно добавить только разрешения уровня сервера. Для составления списка разрешений уровня сервера, выполните следующее выражение. Разрешениями уровня сервера являются:  
  
```sql  
SELECT * FROM sys.fn_builtin_permissions('SERVER') ORDER BY permission_name;  
```  
  
 Дополнительные сведения о разрешениях см. в разделах [Разрешения (ядро СУБД)](../permissions-database-engine.md) и [sys.fn_builtin_permissions (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql).  
  
## <a name="working-with-server-level-roles"></a>Работа с ролями уровня сервера  
 В следующей таблице описаны команды, представления и функции, предназначенные для работы с ролями уровня сервера.  
  
|Компонент|Тип|Описание|  
|-------------|----------|-----------------|  
|[sp_helpsrvrole (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql)|Метаданные|Возвращает список ролей уровня сервера.|  
|[sp_helpsrvrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql)|Метаданные|Возвращает сведения о членах роли уровня сервера.|  
|[sp_srvrolepermission (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql)|Метаданные|Отображает разрешения роли уровня сервера.|  
|[Функция IS_SRVROLEMEMBER (Transact-SQL)](/sql/t-sql/functions/is-srvrolemember-transact-sql)|Метаданные|Указывает, является ли имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] членом указанной роли уровня сервера.|  
|[sys.server_role_members (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)|Метаданные|Возвращает одну строку для каждого члена каждой роли уровня сервера.|  
|[sp_addsrvrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql)|Command|Добавляет имя входа в качестве члена роли уровня сервера. Устарело. Используйте вместо этого [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .|  
|[sp_dropsrvrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql)|Command|Удаляет из роли уровня сервера имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] либо пользователя или группу Windows. Устарело. Используйте вместо этого [ALTER SERVER ROLE](/sql/t-sql/statements/alter-server-role-transact-sql) .|  
|[CREATE SERVER ROLE (Transact-SQL)](/sql/t-sql/statements/create-server-role-transact-sql)|Command|Создает определяемую пользователем роль сервера.|  
|[ALTER SERVER ROLE (Transact-SQL)](/sql/t-sql/statements/alter-server-role-transact-sql)|Command|Изменяет членство в роли сервера или изменяет имя определяемой пользователем роли сервера.|  
|[DROP SERVER ROLE (Transact-SQL)](/sql/t-sql/statements/drop-server-role-transact-sql)|Command|Удаляет определяемую пользователем роль сервера.|  
|[Функция IS_SRVROLEMEMBER (Transact-SQL)](/sql/t-sql/functions/is-srvrolemember-transact-sql)|Компонент|Определяет членство роли сервера.|  
  
## <a name="see-also"></a>См. также  
 [Роли уровня базы данных](../authentication-access/database-level-roles.md)   
 [Представления каталога безопасности (Transact-SQL)](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)   
 [Функции безопасности (Transact-SQL)](/sql/t-sql/functions/security-functions-transact-sql)   
 [Обеспечение безопасности SQL Server](../securing-sql-server.md)   
 [GRANT, предоставление разрешений участникам на уровне сервера (Transact-SQL)](/sql/t-sql/statements/grant-server-principal-permissions-transact-sql)   
 [REVOKE, отмена разрешений участника на уровне сервера (Transact-SQL)](/sql/t-sql/statements/revoke-server-principal-permissions-transact-sql)   
 [DENY, запрет разрешения участника на уровне сервера (Transact-SQL)](/sql/t-sql/statements/deny-server-principal-permissions-transact-sql)   
 [Создание роли сервера](../authentication-access/create-a-server-role.md)  
  
  
