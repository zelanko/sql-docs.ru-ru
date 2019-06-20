---
title: sp_droprolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprolemember_TSQL
- sp_droprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprolemember
ms.assetid: c2f19ab1-e742-4d56-ba8e-8ffd40cf4925
ms.author: vanto
author: VanMSFT
manager: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c235c23ac0be8dcaf6dc57dae14be9732f5c09f8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822440"
---
# <a name="spdroprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет в текущей базе данных учетную запись безопасности из роли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) вместо этого.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  

### <a name="syntax-for-both-sql-server-and-azure-sql-database"></a>Синтаксис для SQL Server и база данных Azure SQL

```  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  

### <a name="syntax-for-both-azure-sql-data-warehouse-and-parallel-data-warehouse"></a>Синтаксис для хранилища данных Azure SQL и Parallel Data Warehouse

```  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'` — Имя роли, из которой удаляется член. *роль* — **sysname**, не имеет значения по умолчанию. *роль* должен существовать в текущей базе данных.  
  
`[ @membername = ] 'security_account'` Удаляется имя учетной записи безопасности из роли. *security_account* — **sysname**, не имеет значения по умолчанию. *security_account* может быть пользователем базы данных, другой ролью базы данных, имя входа Windows или группу Windows. *security_account* должен существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 sp_droprolemember удаляет члена роли базы данных путем удаления строки из таблицы sysmembers. При удалении члена из роли он теряет все разрешения, которые имел как член этой роли.  
  
 Чтобы удалить пользователя из предопределенной роли сервера, используйте sp_dropsrvrolemember. Пользователи не могут быть удалены из роли public и невозможно удалить ни из какой роли dbo.  
  
 Позволяет просмотреть список членов sp_helpuser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] роли и используйте ALTER ROLE, для добавления члена к роли.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER на эту роль.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится удаление пользователя `JonB` из роли `Sales`.  
  
```sql
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере производится удаление пользователя `JonB` из роли `Sales`.  
  
```sql
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

