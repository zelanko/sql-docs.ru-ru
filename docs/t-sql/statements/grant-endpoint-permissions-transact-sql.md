---
title: GRANT, предоставление разрешений на конечные точки (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- endpoints [SQL Server], permissions
- granting permissions [SQL Server], endpoints
- GRANT statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 9eda885c-fc3a-4c9d-8de6-ce07fb35a934
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c6fcbf78c03bd1f4d9f880abf216c977fcfc309d
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633750"
---
# <a name="grant-endpoint-permissions-transact-sql"></a>GRANT, предоставление разрешений на конечные точки (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешения на конечные точки.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
GRANT permission  [ ,...n ] ON ENDPOINT :: endpoint_name  
        TO < server_principal >  [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Определяет разрешения, на конечную точку, которые могут быть предоставлены. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON ENDPOINT **::** _endpoint_name_  
 Указывает конечную точку, на которую предоставляется разрешение. Квалификатор области ( **::** ) является обязательным.  
  
 TO \<server_principal>  
 Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа, которому будут представлены разрешения.  
  
 *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданное из имени входа Windows.  
  
 *SQL_Server_login_from_certificate*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с сертификатом.  
  
 *SQL_Server_login_from_AsymKey*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с ассиметричным ключом.  
  
 WITH GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
 AS *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с использованием которого участник, выполняющий этот запрос, осуществляет свое право на предоставление разрешений.  
  
## <a name="remarks"></a>Remarks  
 Разрешения в области сервера предоставляются только в том случае, если текущей базой данных является **master**.  
  
 Сведения о конечных точках отображаются в представлении каталога [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md). Сведения о серверных разрешениях отображаются в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md), а сведения о серверах-участниках — в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Конечная точка — это защищаемый объект на уровне сервера. Наиболее специфичные и ограниченные разрешения, которые могут быть выданы на конечную точку, перечислены в следующей таблице, вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение конечной точки|Содержится в разрешении конечной точки|Подразумевается в разрешении сервера|  
|-------------------------|------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY ENDPOINT|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL в конечной точке или разрешения ALTER ANY ENDPOINT на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-view-definition-permission-on-an-endpoint"></a>A. Предоставление разрешения VIEW DEFINITION на конечную точку  
 В следующем примере предоставлено разрешение `VIEW DEFINITION` на конечную точку `Mirror7` для учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от `ZArifin`.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>Б. Предоставление разрешения TAKE OWNERSHIP с параметром GRANT OPTION  
 В следующем примере предоставляется разрешение `TAKE OWNERSHIP` на конечную точку `Shipping83` для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от `PKomosinski` с `GRANT OPTION`.  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [DENY, запрет разрешений на конечную точку (Transact-SQL)](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на конечную точку (Transact-SQL)](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Представления каталога конечных точек (Transact-SQL)](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
