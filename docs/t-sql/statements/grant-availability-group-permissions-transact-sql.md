---
title: GRANT (разрешения на группу доступности)
description: Предоставляет разрешения на группу доступности Always On.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 06/12/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], permissions
- GRANT statement, availability groups
- granting permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 060eb839-666a-4046-9e1d-5edc9ea75a11
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0a9954e823ae66017c3a6105f0f0ec27964b7043
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246165"
---
# <a name="grant-availability-group-permissions-transact-sql"></a>GRANT (предоставление) разрешений группы доступности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешения на группу доступности AlwaysOn.  
  

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
 *permission*  
 Указывает разрешение, которое может быть предоставлено для группы доступности. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 ON AVAILABILITY GROUP **::** _availability_group_name_  
 Указывает группу доступности, для которой предоставляется разрешение. Квалификатор области ( **::** ) является обязательным.  
  
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
  
 Сведения о группах доступности отображаются в представлении каталога [sys.availability_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md). Сведения о серверных разрешениях отображаются в представлении каталога [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md), а сведения о серверах-участниках — в представлении каталога [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Группа доступности защищается на уровне сервера. В следующей таблице указаны конкретные, ограниченные разрешения, которые могут быть предоставлены для группы доступности, а также более общие разрешения, неявно включающие первую категорию разрешений.  
  
|Разрешения группы доступности|Подразумевается в разрешении группы доступности|Подразумевается в разрешении сервера|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
 Схему всех разрешений [!INCLUDE[ssDE](../../includes/ssde-md.md)] см. в [афише разрешений компонента Database Engine](https://aka.ms/sql-permissions-poster).  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL для группы доступности или разрешения ALTER ANY AVAILABILITY GROUP для сервера.  
  
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
 Следующий код предоставляет разрешение  `CONTROL` в группе доступности `MyAg`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователю `PKomosinski`. Разрешение CONTROL дает пользователю полный контроль над группой доступности, даже если он не является владельцем группы доступности. Инструкции по изменению владельца базы данных см. в статье [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [REVOKE, отзыв разрешений на группу доступности (Transact-SQL)](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [DENY, запрет разрешений на группу доступности (Transact-SQL)](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Представления каталога групп доступности AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md) [Разрешения &#40;ядро СУБД&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
