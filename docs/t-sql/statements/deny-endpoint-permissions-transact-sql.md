---
title: DENY, запрет разрешений на конечную точку (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/15/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- endpoints [SQL Server], permissions
- DENY statement, endpoints
- denying permissions [SQL Server], endpoints
- permissions [SQL Server], endpoints
ms.assetid: 3ac40457-7529-4eda-95a4-5247345cc8cf
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b2599cd81950f20b8f1771e5508318955fd8eb80
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54326315"
---
# <a name="deny-endpoint-permissions-transact-sql"></a>DENY, запрет разрешений на конечную точку (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запрещает выполнение тех или иных операций над конечной точкой.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission  [ ,...n ] ON ENDPOINT :: endpoint_name  
    TO < server_principal >  [ ,...n ]  
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
 Разрешение на выполнение операций над конечной точкой, которое может быть запрещено. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON ENDPOINT **::**_endpoint_name_  
 Конечная точка, разрешение на работу с которой блокируется. Квалификатор области (**::**) является обязательным.  
  
 TO \<server_principal>  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которого запрещается разрешение.  
  
 *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданное из имени входа Windows.  
  
 *SQL_Server_login_from_certificate*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с сертификатом.  
  
 *SQL_Server_login_from_AsymKey*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сопоставленного с ассиметричным ключом.  
  
 CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
 AS *SQL_Server_login*  
 Задает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], по которому субъект, выполняющий этот запрос, получает право запретить разрешение.  
  
## <a name="remarks"></a>Remarks  
 Разрешения на уровне сервера можно запрещать только в том случае, если текущей базой данных является **master**.  
  
 Сведения о конечных точках отображаются в представлении каталога [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md). Сведения о серверных разрешениях отображаются в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md), а сведения о серверах-участниках — в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Конечная точка — это защищаемый объект на уровне сервера. Самые специфичные и ограниченные разрешения на работу с конечной точкой, в которые можно запрещать, приведены в следующей таблице вместе с общими разрешениями, неявно их охватывающими.  
  
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
  
### <a name="a-denying-view-definition-permission-on-an-endpoint"></a>A. Запрет разрешения VIEW DEFINITION на конечной точке  
 Следующий код запрещает разрешение `VIEW DEFINITION`, связанное с конечной точкой `Mirror7`, для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем `ZArifin`.  
  
```  
USE master;  
DENY VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-cascade-option"></a>Б. Запрет разрешения TAKE OWNERSHIP с аргументом CASCADE  
 Следующий код запрещает разрешение `TAKE OWNERSHIP`, связанное с конечной точкой `Shipping83`, для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` и всех участников, которым `PKomosinski` предоставил разрешение `TAKE OWNERSHIP`.  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений конечной точке (Transact-SQL)](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на конечную точку (Transact-SQL)](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Представления каталога конечных точек (Transact-SQL)](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
