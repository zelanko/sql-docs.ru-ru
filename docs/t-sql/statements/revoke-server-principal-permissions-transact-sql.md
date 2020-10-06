---
title: REVOKE (разрешения на субъект сервера)
description: Отмена разрешений для имени входа SQL Server.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, impersonation
- permissions [SQL Server], impersonation
- permissions [SQL Server], logins
- impersonate [SQL Server], revoking
- logins [SQL Server], revoking
- REVOKE statement, logins
ms.assetid: 75409024-f150-4326-af16-9d60e900df18
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1e2b53af6fd42d77e2169862074ac61c63dc5042
ms.sourcegitcommit: b93beb4f03aee2c1971909cb1d15f79cd479a35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498007"
---
# <a name="revoke-server-principal-permissions-transact-sql"></a>REVOKE, отмена разрешений участника на уровне сервера (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отменяет разрешения, выданные или запрещенные для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] }   
    ON   
    { [ LOGIN :: SQL_Server_login ]  
      | [ SERVER ROLE :: server_role ] }   
    { FROM | TO } <server_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
    SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey     
    | server_role  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *permission*  
 Указывает разрешение, которое может быть отменено для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 LOGIN **::** *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для которой отменяются разрешения. Квалификатор области ( **::** ) является обязательным.  
  
 SERVER ROLE **::** *server_role*  
 Указывает роль сервера, для которой отменяется разрешение. Квалификатор области ( **::** ) является обязательным.  
  
 { FROM | TO } \<server_principal>. Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или роль сервера, для которых отменяется разрешение.  
  
 *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданное из имени входа Windows.  
  
 *SQL_Server_login_from_certificate*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с сертификатом.  
  
 *SQL_Server_login_from_AsymKey*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с ассиметричным ключом.  
  
 *server_role*  
 Указывает имя определяемой пользователем роли сервера.  
  
 GRANT OPTION  
 Показывает, что отменяется право на предоставление указанного разрешения другим участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], от которого участник, выполняющий этот запрос, получает право отмены разрешения.  
  
## <a name="remarks"></a>Remarks  
 Имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и роли сервера являются защищаемыми объектами уровня сервера. Наиболее специфичные и ограниченные разрешения, которые могут быть отменены для имени входа или роли сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение для имени входа SQL Server или роли сервера|Содержится в разрешении для имени входа SQL Server или роли сервера|Подразумевается в разрешении сервера|  
|------------------------------------------------|-----------------------------------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL SERVER|  
|IMPERSONATE|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
|ALTER|CONTROL|ALTER ANY LOGIN<br /><br /> ALTER ANY SERVER ROLE|  
  
## <a name="permissions"></a>Разрешения  
 Для имен входа требуется разрешение CONTROL на имя входа или разрешение ALTER ANY LOGIN на сервер.  
  
 Для ролей сервера требуется разрешение CONTROL на роль сервера или разрешение ALTER ANY SERVER ROLE на сервер.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-revoking-impersonate-permission-on-a-login"></a>A. Отмена разрешения IMPERSONATE на имя входа  
 Следующий пример отменяет разрешение `IMPERSONATE` на имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`WanidaBenshoof` для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданного из пользователя Windows `AdvWorks\YoonM`.  
  
```sql  
USE master;  
REVOKE IMPERSONATE ON LOGIN::WanidaBenshoof FROM [AdvWorks\YoonM];  
GO  
```  
  
### <a name="b-revoking-view-definition-permission-with-cascade"></a>Б. Отмена разрешения VIEW DEFINITION с параметром CASCADE  
 Следующий пример отменяет разрешение `VIEW DEFINITION` для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`EricKurjan` от имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`RMeyyappan`. Параметр `CASCADE` показывает, что разрешение `VIEW DEFINITION` для `EricKurjan` будет также отменено для участников, которым `RMeyyappan` предоставил это разрешение.  
  
```sql  
USE master;  
REVOKE VIEW DEFINITION ON LOGIN::EricKurjan FROM RMeyyappan   
    CASCADE;  
GO   
```  
  
### <a name="c-revoking-view-definition-permission-on-a-server-role"></a>В. Отмена разрешения VIEW DEFINITION для роли сервера  
 В следующем примере разрешение `VIEW DEFINITION` для роли сервера `Sales` отменяется для роли сервера `Auditors`.  
  
```sql  
USE master;  
REVOKE VIEW DEFINITION ON SERVER ROLE::Sales TO Auditors ;  
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [GRANT, предоставление разрешений участникам на уровне сервера (Transact-SQL)](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)   
 [DENY, запрет разрешения участника на уровне сервера (Transact-SQL)](../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)   
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  

