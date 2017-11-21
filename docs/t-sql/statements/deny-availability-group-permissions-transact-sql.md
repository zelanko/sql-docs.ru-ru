---
title: "DENY, запрет разрешений группы доступности (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/15/2017
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
- Availability Groups [SQL Server], permissions
- permissions [SQL Server], availability group
- DENY statement, availability groups
- denying permissions, [SQL Server], availability groups
ms.assetid: bda60b36-a0b9-4c20-80c1-6a5cb1d638a5
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d2e96c60c2811f0a0a87de3d50e3567cd8655cf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-availability-group-permissions-transact-sql"></a>DENY (Отмена) разрешений группы доступности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Запрещает разрешения на группу доступности AlwaysOn в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission  [ ,...n ] ON AVAILABILITY GROUP :: availability_group_name  
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
 Указывает разрешение, которое может быть запрещено для группы доступности. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 В ГРУППЕ ДОСТУПНОСТИ **::***availability_group_name*  
 Указывает группу доступности, для которой будет запрещено разрешение. Квалификатор области (**::**) является обязательным.  
  
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
  
 Сведения о группах доступности можно увидеть в [sys.availability_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) представления каталога. Сведения о разрешениях сервера можно увидеть в [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) представления каталога и сведения об участниках сервера отобразится в [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления каталога.  
  
 Группа доступности защищается на уровне сервера. Наиболее конкретные и ограниченные разрешения, в предоставлении которых для группы доступности может быть отказано, перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешения группы доступности|Подразумевается в разрешении группы доступности|Подразумевается в разрешении сервера|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL для группы доступности или разрешения ALTER ANY AVAILABILTIY GROUP для сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-denying-view-definition-permission-on-an-availability-group"></a>A. Запрет разрешения VIEW DEFINITION для группы доступности  
 Следующий код запрещает разрешение `VIEW DEFINITION`, связанное с группой доступности `MyAg`, для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем `ZArifin`.  
  
```  
USE master;  
DENY VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-the-cascade-option"></a>Б. Запрет разрешения TAKE OWNERSHIP с аргументом CASCADE  
 В следующем примере запрещается разрешение `TAKE OWNERSHIP` для группы доступности `MyAg` для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` с аргументом `CASCADE`.  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Группа доступности REVOKE разрешения &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [Группа доступности ПРЕДОСТАВЬТЕ разрешения &#40; Transact-SQL &#41;](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

