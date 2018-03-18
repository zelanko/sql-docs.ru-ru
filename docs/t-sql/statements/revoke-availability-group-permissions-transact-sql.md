---
title: "REVOKE, отмена разрешений группы доступности (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
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
- Availability Groups [SQL Server], permissions
- REVOKE statement, availability groups
- revoking permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 02c77378-a36d-4286-9235-d8867a2b92ad
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f7bd88af97183e7cb5f3bd36a4bc5194be62a4d6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="revoke-availability-group-permissions-transact-sql"></a>REVOKE (отзыв) разрешений группы доступности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Отменяет разрешения для группы доступности AlwaysOn. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON AVAILABILITY GROUP :: availability_group_name  
    { FROM | TO } < server_principal >  [ ,...n ]  
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
 Указывает разрешение, которое может быть отменено для группы доступности. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON AVAILABILITY GROUP **::***availability_group_name*  
 Указывает группу доступности, для которой отменяется разрешение. Квалификатор области (**::**) является обязательным.  
  
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
  
> [!IMPORTANT]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *SQL_Server_login*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], от которого участник, выполняющий этот запрос, получает право отмены разрешения.  
  
## <a name="remarks"></a>Remarks  
 Разрешения на уровне сервера могут быть отозваны, только если текущей базой данных является **master**.  
  
 Сведения о группах доступности отображаются в представлении каталога [sys.availability_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md). Сведения о серверных разрешениях отображаются в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md), а сведения о серверах-участниках — в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Группа доступности защищается на уровне сервера. В следующей таблице указаны конкретные, ограниченные разрешения, которые могут быть отменены для группы доступности, а также более общие разрешения, неявно включающие первую категорию разрешений.  
  
|Разрешения группы доступности|Подразумевается в разрешении группы доступности|Подразумевается в разрешении сервера|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL для группы доступности или разрешения ALTER ANY AVAILABILTIY GROUP для сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-revoking-view-definition-permission-on-an-availability-group"></a>A. Отмена разрешения VIEW DEFINITION для группы доступности  
 Следующий код отменяет разрешение `VIEW DEFINITION` на группу доступности `MyAg` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя `ZArifin`.  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-revoking-take-ownership-permission-with-the-cascade"></a>Б. Отмена разрешения TAKE OWNERSHIP с параметром CASCADE  
 В следующем примере отменяется разрешение `TAKE OWNERSHIP` в группе доступности `MyAg` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для пользователя `PKomosinski` и для всех участников, которым пользователь `PKomosinski` предоставил разрешение TAKE OWNERSHIP для группы доступности MyAg.  
  
```  
USE master;  
REVOKE TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
### <a name="c-revoking-a-previously-granted-with-grant-option-clause"></a>В. Отмена ранее предоставленного разрешения с предложением WITH GRANT OPTION  
 Если разрешение было предоставлено с предложением WITH GRANT OPTION, используйте REVOKE GRANT OPTION FOR… для удаления параметра WITH GRANT OPTION. В следующем примере предоставляется разрешение, из которого затем удаляется параметр WITH GRANT OPTION.  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    WITH GRANT OPTION;  
GO  
REVOKE GRANT OPTION FOR CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski  
CASCADE  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на группу доступности (Transact-SQL)](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [DENY, запрет разрешений на группу доступности (Transact-SQL)](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

