---
title: "GRANT, предоставление разрешений участникам на уровне сервера (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- impersonate [SQL Server], granting
- granting permissions [SQL Server], logins
- permissions [SQL Server], impersonate
- permissions [SQL Server], logins
- GRANT statement, impersonation
- GRANT statement, logins
- logins [SQL Server], granting access
- granting permissions [SQL Server], impersonation
ms.assetid: 4cbed281-5e1e-4d8b-b410-4c18a6cd0205
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9dfd348b6e19f289e41217df4b35dd4cf6e90712
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="grant-server-principal-permissions-transact-sql"></a>GRANT, предоставление разрешений участникам на уровне сервера (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешения для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GRANT permission [ ,...n ] }   
    ON   
    { [ LOGIN :: SQL_Server_login ]  
      | [ SERVER ROLE :: server_role ] }   
    TO <server_principal> [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
    SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey   
    | server_role  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Указывает разрешение, которое может быть выдано для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 LOGIN **::** *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которому предоставляется разрешение. Квалификатор области (**::**) является обязательным.  
  
 SERVER ROLE **::** *server_role*  
 Указывает определяемую пользователем роль сервера, которой предоставляется разрешение. Квалификатор области (**::**) является обязательным.  
  
 TO \<server_principal> Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или роль сервера, которой представляется разрешение.  
  
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
  
 WITH GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
 AS *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с использованием которого участник, выполняющий этот запрос, осуществляет свое право на предоставление разрешений.  
  
## <a name="remarks"></a>Remarks  
 Разрешения в области сервера предоставляются только в том случае, если текущей база данных является master.  
  
 Данные о разрешениях сервера отображаются в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md). Данные о серверах-участниках отображаются в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и роли сервера являются защищаемыми объектами уровня сервера. Наиболее специфичные и ограниченные разрешения, которые могут быть выданы для имени входа или роли сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
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
  
### <a name="a-granting-impersonate-permission-on-a-login"></a>A. Выдача разрешения IMPERSONATE для имени входа  
 В следующем примере разрешение `IMPERSONATE` для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `WanidaBenshoof` выдается имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданному на основе пользователя Windows `AdvWorks\YoonM`.  
  
```  
USE master;  
GRANT IMPERSONATE ON LOGIN::WanidaBenshoof to [AdvWorks\YoonM];  
GO  
```  
  
### <a name="b-granting-view-definition-permission-with-grant-option"></a>Б. Выдача разрешения VIEW DEFINITION с параметром GRANT OPTION  
 В следующем примере разрешение `VIEW DEFINITION` для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `EricKurjan` выдается имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `RMeyyappan` с параметром `GRANT OPTION`.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON LOGIN::EricKurjan TO RMeyyappan   
    WITH GRANT OPTION;  
GO   
```  
  
### <a name="c-granting-view-definition-permission-on-a-server-role"></a>В. Предоставление разрешения VIEW DEFINITION на роль сервера  
 В следующем примере разрешение `VIEW DEFINITION` для роли сервера `Sales` предоставляется роли сервера `Auditors`.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON SERVER ROLE::Sales TO Auditors ;  
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  

