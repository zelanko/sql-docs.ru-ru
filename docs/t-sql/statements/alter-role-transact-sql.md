---
title: ALTER ROLE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_ROLE_TSQL
- ALTER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database roles
- ALTER ROLE statement
- renaming database roles
- database roles [SQL Server], modifying
- names [SQL Server], database roles
ms.assetid: e1e83caa-17cc-4871-b2db-2711339fb64f
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d2adf7404e80a0a04932c14b598011c1799b5611
ms.sourcegitcommit: 94f6a4b506dfda242fc3efb2403847e22a36d340
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546576"
---
# <a name="alter-role-transact-sql"></a>ALTER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет члены в роль базы данных или удаляет их из нее либо изменяет имя определяемой пользователем роли базы данных.  
  
> [!NOTE]  
>  Для изменения ролей или удаления членов в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] используйте хранимые процедуры [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) и [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server (starting with 2012) and Azure SQL Database  
  
ALTER ROLE  role_name  
{  
       ADD MEMBER database_principal  
    |  DROP MEMBER database_principal  
    |  WITH NAME = new_name  
}  
[;]  
```  
  
 
```  
-- Syntax for SQL Server 2008, Azure SQL Data Warehouse and Parallel Data Warehouse
  
-- Change the name of a user-defined database role  
ALTER ROLE role_name   
    WITH NAME = new_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *role_name*  
 **ПРИМЕНИМО К**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2008), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает роль базы данных, которую нужно изменить.  
  
 ADD MEMBER *database_principal*  
 **ПРИМЕНИМО К**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2012), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает на добавление участника базы данных к членству в роли базы данных.  
  
-   *database_principal* является пользователем базы данных или ролью базы данных, определяемой пользователем.  
  
-   *database_principal* не может быть предопределенной ролью базы данных или участником на уровне сервера.  
  
DROP MEMBER *database_principal*  
 **ПРИМЕНИМО К**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2012), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает на удаление участника базы из членства в роли базы данных.  
  
-   *database_principal* является пользователем базы данных или ролью базы данных, определяемой пользователем.  
  
-   *database_principal* не может быть предопределенной ролью базы данных или участником на уровне сервера.  
  
WITH NAME = *new_name*  
 **ПРИМЕНИМО К**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2008), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает на изменение имени определяемой пользователем роли базы данных. Новое имя еще не должно существовать в базе данных.  
  
 Изменение имени роли базы данных не изменяет идентификационный номер, владельца или разрешения роли.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой команды необходимо одно или несколько из указанных далее разрешений или членств.  
  
-   Разрешение **ALTER** для роли  
-   Разрешение **ALTER ANY ROLE** для базы данных  
-   Членство в предопределенной роли базы данных **db_securityadmin**  
  
Кроме того, чтобы изменить членство в предопределенной роли базы данных, требуется:  
  
-   членство в предопределенной роли базы данных **db_owner**.  
  
## <a name="limitations-and-restrictions"></a>ограничения  
 Имя предопределенной роли базы данных изменить нельзя.  
  
## <a name="metadata"></a>Метаданные  
 Приведенные далее системные представления содержат сведения о ролях базы данных и участниках базы данных.  
  
-   [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
-   [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-change-the-name-of-a-database-role"></a>A. Изменение имени роли базы данных  
 **ПРИМЕНИМО К**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2008), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 В следующем примере изменяется имя роли `buyers` на `purchasing`.   Для этого примера используется образец базы данных [AdventureWorks](https://msftdbprodsamples.codeplex.com/).
  
```sql  
ALTER ROLE buyers WITH NAME = purchasing;  
```  
  
### <a name="b-add-or-remove-role-members"></a>Б. Добавление или удаление членов роли  
 **ПРИМЕНИМО К**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2012), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 В этом примере создается роль базы данных с именем `Sales`. В нем показано добавление пользователя базы данных Barry в членство и затем демонстрируется удаление Barry.   Для этого примера используется образец базы данных [AdventureWorks](https://msftdbprodsamples.codeplex.com/).
  
```sql  
CREATE ROLE Sales;  
ALTER ROLE Sales ADD MEMBER Barry;  
ALTER ROLE Sales DROP MEMBER Barry;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE ROLE (Transact-SQL)](../../t-sql/statements/create-role-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE (Transact-SQL)](../../t-sql/statements/drop-role-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
