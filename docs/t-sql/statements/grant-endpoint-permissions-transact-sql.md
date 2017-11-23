---
title: "Разрешения GRANT Endpoint (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/17/2017
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
- endpoints [SQL Server], permissions
- granting permissions [SQL Server], endpoints
- GRANT statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 9eda885c-fc3a-4c9d-8de6-ce07fb35a934
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9106f72b1e7d8c137b4a2f80d332db87750309ee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="grant-endpoint-permissions-transact-sql"></a>GRANT, предоставление разрешений на конечные точки (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешения на конечные точки.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 *разрешение*  
 Определяет разрешения, на конечную точку, которые могут быть предоставлены. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 В конечной ТОЧКЕ **::***endpoint_name*  
 Указывает конечную точку, на которую предоставляется разрешение. Квалификатор области (**::**) является обязательным.  
  
 Чтобы \<server_principal >  
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
  
## <a name="remarks"></a>Замечания  
 Разрешения в области сервера могут предоставляться только в том случае, когда текущая база данных **master**.  
  
 Сведения о конечных точках видны в [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md) представления каталога. Сведения о разрешениях сервера можно увидеть в [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) представления каталога и сведения об участниках сервера отобразится в [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления каталога.  
  
 Конечная точка — это защищаемый объект на уровне сервера. Наиболее специфичные и ограниченные разрешения, которые могут быть выданы на конечную точку, перечислены в следующей таблице, вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение конечной точки|Содержится в разрешении конечной точки|Подразумевается в разрешении сервера|  
|-------------------------|------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY ENDPOINT|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL в конечной точке или разрешения ALTER ANY ENDPOINT на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-view-definition-permission-on-an-endpoint"></a>A. Предоставление разрешения VIEW DEFINITION на конечную точку  
 В следующем примере предоставлено разрешение `VIEW DEFINITION` на конечную точку `Mirror7` для учетной записи `ZArifin` от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE master;  
GRANT VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>Б. Предоставление разрешения TAKE OWNERSHIP с параметром GRANT OPTION  
 В следующем примере предоставляется разрешение `TAKE OWNERSHIP` на конечную точку `Shipping83` для пользователя `PKomosinski` от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с `GRANT OPTION`.  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ЗАПРЕТ разрешений на конечные точки &#40; Transact-SQL &#41;](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения конечной точки &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Представления каталога конечных точек &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.Endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
