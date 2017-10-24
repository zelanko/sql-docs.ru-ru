---
title: "ЗАПРЕТ разрешений на конечные точки (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- endpoints [SQL Server], permissions
- DENY statement, endpoints
- denying permissions [SQL Server], endpoints
- permissions [SQL Server], endpoints
ms.assetid: 3ac40457-7529-4eda-95a4-5247345cc8cf
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a263d6a5a576b4f4e06bb44a6c6fb40c99e64660
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-endpoint-permissions-transact-sql"></a>DENY, запрет разрешений на конечную точку (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 *разрешение*  
 Разрешение на выполнение операций над конечной точкой, которое может быть запрещено. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 В конечной ТОЧКЕ **::***endpoint_name*  
 Конечная точка, разрешение на работу с которой блокируется. Квалификатор области (**::**) является обязательным.  
  
 Чтобы \<server_principal >  
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
 Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, от которого участник, выполняющий этот запрос получает право на запрет разрешения.  
  
## <a name="remarks"></a>Замечания  
 Разрешения на уровне сервера может быть отклонен, только в том случае, если текущая база данных **master**.  
  
 Сведения о конечных точках видны в [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md) представления каталога. Сведения о разрешениях сервера можно увидеть в [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) представления каталога и сведения об участниках сервера отобразится в [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления каталога.  
  
 Конечная точка — это защищаемый объект на уровне сервера. Самые специфичные и ограниченные разрешения на работу с конечной точкой, в которые можно запрещать, приведены в следующей таблице вместе с общими разрешениями, неявно их охватывающими.  
  
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
  
### <a name="a-denying-view-definition-permission-on-an-endpoint"></a>A. Запрет разрешения VIEW DEFINITION на конечной точке  
 В следующем примере запрещается `VIEW DEFINITION` разрешений на конечную точку `Mirror7` для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа `ZArifin`.  
  
```  
USE master;  
DENY VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-cascade-option"></a>Б. Запрет разрешения TAKE OWNERSHIP с аргументом CASCADE  
 В следующем примере запрещается `TAKE OWNERSHIP` разрешений на конечную точку `Shipping83` для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователя `PKomosinski` и для участников, которым `PKomosinski` предоставлены `TAKE OWNERSHIP`.  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений конечной точке (Transact-SQL)](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения конечной точки &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Представления каталога конечных точек &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.Endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

