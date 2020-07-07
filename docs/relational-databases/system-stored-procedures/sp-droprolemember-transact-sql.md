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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8be7e84ccd80d80c1345adec3450e5bc8e0f4da6
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012707"
---
# <a name="sp_droprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Удаляет в текущей базе данных учетную запись безопасности из роли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [инструкцию ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  

### <a name="syntax-for-both-sql-server-and-azure-sql-database"></a>Синтаксис как для SQL Server, так и для базы данных SQL Azure

```  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  

### <a name="syntax-for-both-azure-sql-data-warehouse-and-parallel-data-warehouse"></a>Синтаксис хранилища данных SQL Azure и параллельного хранилища данных

```  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'`Имя роли, из которой удаляется элемент. Аргумент *Role* имеет тип **sysname**и не имеет значения по умолчанию. *роль* должна существовать в текущей базе данных.  
  
`[ @membername = ] 'security_account'`Имя учетной записи безопасности, удаляемой из роли. Аргумент *security_account* имеет тип **sysname**и не имеет значения по умолчанию. *security_account* может быть пользователь базы данных, другая роль базы данных, имя входа Windows или группа Windows. *security_account* должен существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 sp_droprolemember исключает члена из роли базы данных, удаляя строку из таблицы sysmembers. При удалении члена из роли он теряет все разрешения, которые имел как член этой роли.  
  
 Для удаления пользователя из предопределенной роли сервера пользуйтесь хранимой процедурой sp_dropsrvrolemember. Пользователи не могут быть удалены из роли public, а dbo не может быть удален из какой-либо роли.  
  
 Используйте sp_helpuser для просмотра членов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] роли и с помощью инструкции ALTER ROLE добавьте член в роль.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER на эту роль.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится удаление пользователя `JonB` из роли `Sales`.  
  
```sql
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере производится удаление пользователя `JonB` из роли `Sales`.  
  
```sql
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

