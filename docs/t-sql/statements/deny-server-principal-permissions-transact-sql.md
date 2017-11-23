---
title: "Запрет разрешения участника на уровне сервера (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- DENY statement, impersonate
- permissions [SQL Server], impersonate
- impersonate [SQL Server], denying
- DENY statement, logins
- permissions [SQL Server], logins
- denying permissions [SQL Server], logins
- servers [SQL Server], permissions
- logins [SQL Server], denying access
ms.assetid: 859affa7-0567-47d1-9490-57c1abbd619b
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 795c7dcc946966859e5d81382df75a4bb646e38d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="deny-server-principal-permissions-transact-sql"></a>DENY, запрет разрешения участника на уровне сервера (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запрещает разрешения, предоставленные для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission [ ,...n ] }   
    ON   
    { [ LOGIN :: SQL_Server_login ]  
      | [ SERVER ROLE :: server_role ] }   
    TO <server_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
    SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey   
    | server_role  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Определяет разрешение, т.е. доступ, который запрещается для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 Имя входа **::** *SQL_Server_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого разрешение запрещается. Квалификатор области (**::**) является обязательным.  
  
 РОЛЬ сервера **::** *server_role*  
 Указывает роль сервера, для которой запрещается разрешение. Квалификатор области (**::**) является обязательным.  
  
 Чтобы \<server_principal >  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или роль сервера, которой представляется разрешение.  
  
 Чтобы *SQL_Server_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого запрещается разрешение.  
  
 *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданное из имени входа Windows.  
  
 *SQL_Server_login_from_certificate*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с сертификатом.  
  
 *SQL_Server_login_from_AsymKey*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с ассиметричным ключом.  
  
 *server_role*  
 Название определения роли сервера.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS *SQL_Server_login*  
 Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, от которого участник, выполняющий этот запрос получает право на запрет разрешения.  
  
## <a name="remarks"></a>Замечания  
 Разрешения в области сервера могут запрещаться только в том случае, если текущей базой данных является master.  
  
 Сведения о разрешениях сервера доступен в [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) представления каталога. Сведения об участниках сервера можно найти в [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления каталога.  
  
 Инструкция DENY завершается ошибкой, если не задан аргумент CASCADE, если разрешение запрещается участнику, который предоставлял это разрешение с аргументом GRANT OPTION.  
  
 Имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и роли сервера являются защищаемыми объектами уровня сервера. Наиболее специфичные и ограниченные разрешения, которые могут быть запрещены для имени входа или роли сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение для имени входа SQL Server или роли сервера|Содержится в разрешении для имени входа SQL Server или роли сервера|Подразумевается в разрешении сервера|  
|------------------------------------------------|-----------------------------------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL SERVER|  
|IMPERSONATE|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
|ALTER|CONTROL|ALTER ANY LOGIN<br /><br /> ALTER ANY SERVER ROLE|  
  
## <a name="permissions"></a>Permissions  
 Для имен входа требуется разрешение CONTROL на имя входа или разрешение ALTER ANY LOGIN на сервер.  
  
 Для ролей сервера требуется разрешение CONTROL на роль сервера или разрешение ALTER ANY SERVER ROLE на сервер.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-denying-impersonate-permission-on-a-login"></a>A. Запрещение разрешения IMPERSONATE на имя входа  
 В следующем примере запрещается `IMPERSONATE` разрешение на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа `WanidaBenshoof` для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, созданного из пользователя Windows `AdvWorks\YoonM`.  
  
```  
USE master;  
DENY IMPERSONATE ON LOGIN::WanidaBenshoof TO [AdvWorks\YoonM];  
GO  
```  
  
### <a name="b-denying-view-definition-permission-with-cascade"></a>Б. Запрещение разрешения VIEW DEFINITION с параметром CASCADE  
 В следующем примере производится запрещение разрешения `VIEW DEFINITION` на имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]	`EricKurjan` для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]	`RMeyyappan`. Параметр `CASCADE` указывает, что разрешение `VIEW DEFINITION` на `EricKurjan` будет также запрещено участникам, которым `RMeyyappan` его предоставил ранее.  
  
```  
USE master;  
DENY VIEW DEFINITION ON LOGIN::EricKurjan TO RMeyyappan   
    CASCADE;  
GO   
```  
  
### <a name="c-denying-view-definition-permission-on-a-server-role"></a>В. Запрещение разрешения VIEW DEFINITION для роли сервера  
 В следующем примере разрешение `VIEW DEFINITION` для роли сервера `Sales` запрещается для роли сервера `Auditors`.  
  
```  
USE master;  
DENY VIEW DEFINITION ON SERVER ROLE::Sales TO Auditors ;  
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [GRANT, предоставление разрешений участникам на уровне сервера (Transact-SQL)](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений участника на уровне сервера (Transact-SQL)](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
