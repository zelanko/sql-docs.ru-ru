---
title: DROP ROLE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP ROLE
- DROP_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting roles
- database roles [SQL Server], removing
- removing roles
- DROP ROLE statement
- roles [SQL Server], removing
- dropping roles
ms.assetid: 1f6f13ae-56a2-4ef1-93f5-8e6151b83e1d
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: df52ed86bb11f9c416b610ecc3824b782ad88800
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33066821"
---
# <a name="drop-role-transact-sql"></a>DROP ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Удаляет роль из базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
DROP ROLE [ IF EXISTS ] role_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP ROLE role_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление роли только в том случае, если она уже существует.  
  
 *role_name*  
 Определяет роль, которую следует удалить из базы данных.  
  
## <a name="remarks"></a>Remarks  
 Роли, владеющие объектами защиты, не могут быть удалены из базы данных. Чтобы удалить из базы данных роль, владеющую объектами защиты, необходимо сначала передать эти объекты другому владельцу или удалить их из базы данных. Роли, владеющие объектами защиты, не могут быть удалены из базы данных. Чтобы удалить роль, имеющую члены, необходимо сначала удалить эти члены из данной роли.  
  
 Чтобы удалить члены из роли базы данных, используйте инструкцию [ALTER ROLE (Transact-SQL)](../../t-sql/statements/alter-role-transact-sql.md).  
  
 Удаление предопределенной роли базы данных не может быть осуществлено с помощью инструкции DROP ROLE.  
  
 Сведения о членстве в роли можно просмотреть в представлении каталога sys.database_role_members.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
 Чтобы удалить роль сервера, используйте инструкцию [DROP SERVER ROLE (Transact-SQL)](../../t-sql/statements/drop-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **ALTER ANY ROLE** на базу данных, разрешение **CONTROL** на роль или членство в роли **db_securityadmin**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере роль базы данных `purchasing` удаляется из базы данных `AdventureWorks2012`.  
  
```  
DROP ROLE purchasing;  
GO  
```  
  
  
## <a name="see-also"></a>См. также:  
 [CREATE ROLE (Transact-SQL)](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE (Transact-SQL)](../../t-sql/statements/alter-role-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  


