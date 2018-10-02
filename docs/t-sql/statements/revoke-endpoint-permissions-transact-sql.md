---
title: REVOKE, отмена разрешений на конечные точки (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- endpoints [SQL Server], permissions
- REVOKE statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 826f513e-9ad0-46b9-87ad-7525713638c8
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cad53aef8b06cca5dc37bca1b5a95d82d6c89d74
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839912"
---
# <a name="revoke-endpoint-permissions-transact-sql"></a>REVOKE, отмена разрешений на конечные точки (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет разрешения, предоставленные или запрещенные в конечной точке.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]   
    ON ENDPOINT :: endpoint_name  
    { FROM | TO } <server_principal> [ ,...n ]  
    [ CASCADE ]  
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
  
 ON ENDPOINT **::***endpoint_name*  
 Указывает конечную точку, на которую предоставляется разрешение. Квалификатор области (**::**) является обязательным.  
  
 { FROM | TO } \<server_principal> Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], у которого отменяется разрешение.  
  
 *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданное из имени входа Windows.  
  
 *SQL_Server_login_from_certificate*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с сертификатом.  
  
 *SQL_Server_login_from_AsymKey*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с ассиметричным ключом.  
  
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
 Разрешения на уровне сервера могут быть отозваны, только если текущей базой данных является **master**.  
  
 Сведения о конечных точках отображаются в представлении каталога [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md). Сведения о серверных разрешениях отображаются в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md), а сведения о серверах-участниках — в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Конечная точка — это защищаемый объект на уровне сервера. Наиболее точные и ограниченные разрешения, которые можно отменять в оконечной точке, перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
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
  
### <a name="a-revoking-view-definition-permission-on-an-endpoint"></a>A. Отмена разрешения VIEW DEFINITION в конечной точке  
 В следующем примере отменяется разрешение `VIEW DEFINITION` в конечной точке `Mirror7` из имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `ZArifin`.  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON ENDPOINT::Mirror7 FROM ZArifin;  
GO  
```  
  
### <a name="b-revoking-take-ownership-permission-with-the-cascade-option"></a>Б. Отмена разрешения TAKE OWNERSHIP с параметром CASCADE  
 В следующем примере отменяется разрешение `TAKE OWNERSHIP` в конечной точке `Shipping83` из пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` и из всех участников, которым пользователь `PKomosinski` предоставил разрешение `TAKE OWNERSHIP` для `Shipping83`.  
  
```  
USE master;  
REVOKE TAKE OWNERSHIP ON ENDPOINT::Shipping83 FROM PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений конечной точке (Transact-SQL)](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [DENY, запрет разрешений на конечную точку (Transact-SQL)](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Представления каталога конечных точек (Transact-SQL)](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

