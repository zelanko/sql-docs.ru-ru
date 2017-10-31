---
title: "Разрешения GRANT группы доступности (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/12/2017
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
- Availability Groups [SQL Server], permissions
- GRANT statement, availability groups
- granting permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 060eb839-666a-4046-9e1d-5edc9ea75a11
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 154c99ddfb9f3a69a4a9eeae35f20c5e9720100d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grant-availability-group-permissions-transact-sql"></a>GRANT (предоставление) разрешений группы доступности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Предоставление разрешений для группы доступности Always On.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
GRANT permission  [ ,...n ] ON AVAILABILITY GROUP :: availability_group_name  
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
 Указывает разрешение, которое может быть предоставлено для группы доступности. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 В ГРУППЕ ДОСТУПНОСТИ **::***availability_group_name*  
 Указывает группу доступности, для которой предоставляется разрешение. Квалификатор области (**::**) является обязательным.  
  
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
  
 Сведения о группах доступности можно увидеть в [sys.availability_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) представления каталога. Сведения о разрешениях сервера можно увидеть в [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) представления каталога и сведения об участниках сервера отобразится в [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления каталога.  
  
 Группа доступности защищается на уровне сервера. В следующей таблице указаны конкретные, ограниченные разрешения, которые могут быть предоставлены для группы доступности, а также более общие разрешения, неявно включающие первую категорию разрешений.  
  
|Разрешения группы доступности|Подразумевается в разрешении группы доступности|Подразумевается в разрешении сервера|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
 Для диаграмм всех [!INCLUDE[ssDE](../../includes/ssde-md.md)] разрешения, см. [афише разрешений ядра базы данных](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL для группы доступности или разрешения ALTER ANY AVAILABILTIY GROUP для сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-view-definition-permission-on-an-availability-group"></a>A. Предоставление разрешения VIEW DEFINITION для группы доступности  
 Следующий код предоставляет разрешение `VIEW DEFINITION` в группе доступности `MyAg` для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователя `ZArifin`.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>Б. Предоставление разрешения TAKE OWNERSHIP с параметром GRANT OPTION  
 В следующем примере предоставляется разрешение `TAKE OWNERSHIP` на группу доступности `MyAg` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователю `PKomosinski` с параметром `GRANT OPTION`.  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-control-permission-on-an-availability-group"></a>В. Предоставление разрешения CONTROL для группы доступности  
 Следующий код предоставляет разрешение  `CONTROL` в группе доступности `MyAg` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователю `PKomosinski`. Разрешение CONTROL дает пользователю полный контроль над группой доступности, даже если он не является владельцем группы доступности. Для изменения владельца, в разделе [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Группа доступности REVOKE разрешения &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [ЗАПРЕТ разрешений группы доступности &#40; Transact-SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Представления каталога &#40; групп доступности AlwaysOn Transact-SQL &#41; ](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md) [Разрешения &#40; компонент Database Engine &#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

