---
title: sp_change_users_login (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/13/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_users_login
- sp_change_users_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_users_login
ms.assetid: 1554b39f-274b-4ef8-898e-9e246b474333
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b0c847215d31bd2064467c3edbce42ba957c2e78
ms.sourcegitcommit: f7af758b353b53ac3b596d79fd6e32ad7e1e61cf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79448330"
---
# <a name="sp_change_users_login-transact-sql"></a>sp_change_users_login (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Сопоставляет существующего пользователя базы данных с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
 > [!IMPORTANT]
 > [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Используйте вместо этого [инструкцию ALTER USER](../../t-sql/statements/alter-user-transact-sql.md) .  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_users_login [ @Action = ] 'action'   
    [ , [ @UserNamePattern = ] 'user' ]   
    [ , [ @LoginName = ] 'login' ]   
    [ , [ @Password = ] 'password' ]  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @Action= ] "*действие*"  
 Описывает действие, которое будет выполнено процедурой. *Action* имеет тип **varchar (10)**. *действие* может иметь одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Auto_Fix**|Связывает запись пользователя в системном представлении каталога sys.database_principals в текущей базе данных с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющим такое же имя. Если имени входа с таким же именем не существует, оно будет создано. Проверьте результат инструкции **Auto_Fix** , чтобы убедиться в том, что фактическая ссылка создана. Старайтесь не использовать **Auto_Fix** в ситуациях с учетом безопасности.<br /><br /> При использовании **Auto_Fix**необходимо указать *User* и *Password* , если имя входа еще не существует, в противном случае необходимо указать *User* , но *пароль* будет проигнорирован. *имя для входа* должно быть равно null. *пользователь* должен быть допустимым пользователем в текущей базе данных. Не может быть еще одного пользователя, сопоставленного с именем входа.|  
|**Отчет**|Перечисляет пользователей и соответствующие идентификаторы безопасности (SID) в текущей базе данных, которые не связаны ни с каким именем входа. *пользователь*, *имя для входа*и *пароль* должны быть равны null или не указаны.<br /><br /> Чтобы заменить параметр отчета запросом, использующим системные таблицы, сравните записи в **sys. server_prinicpals** с записями в **sys. database_principals**.|  
|**Update_One**|Связывает указанного *пользователя* в текущей базе данных с существующим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *именем входа*. необходимо указать *пользователя* и *имя для входа* . *пароль* должен быть равен null или не указан.|  
  
 [ @UserNamePattern= ] "*пользователь*"  
 Имя пользователя в текущей базе данных. Аргумент *User* имеет тип **sysname**и значение по умолчанию NULL.  
  
 [ @LoginName= ] "*Login*"  
 Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *Login* имеет тип **sysname**и значение по умолчанию NULL.  
  
 [ @Password= ] "*пароль*"  
 Пароль, назначенный новому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа, которое создается путем указания **Auto_Fix**. Если совпадающее имя входа уже существует, пользователь и имя входа сопоставляются, а *пароль* игнорируется. Если соответствующее имя входа не существует, sp_change_users_login создает новое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и присваивает ему пароль *в качестве пароля* для нового имени входа. Аргумент *Password* имеет тип **sysname**и не должен иметь значение null.  
  
> **ВАЖНО!** Всегда используйте [надежный пароль!](../../relational-databases/security/strong-passwords.md)
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|UserName|**sysname**|Имя пользователя базы данных.|  
|UserSID|**varbinary (85)**|Идентификатор защиты пользователя.|  
  
## <a name="remarks"></a>Remarks  
 Используйте процедуру sp_change_users_login, чтобы связать пользователя базы данных в текущей базе данных с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имя входа для пользователя изменилось, используйте процедуру sp_change_users_login, чтобы связать пользователя с новым именем входа без потери пользовательских разрешений. Новое *имя входа* не может быть SA, а *пользователь* не может быть dbo, Guest или INFORMATION_SCHEMA пользователем.  
  
 Процедура sp_change_users_login не может использоваться для сопоставления пользователей базы данных с участниками уровня Windows, сертификатами или асимметричными ключами.  
  
 Процедуру sp_change_users_login нельзя использовать с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], созданным на основе участника Windows, или с пользователем, созданным с помощью команды CREATE USER WITHOUT LOGIN.  
  
 Процедура sp_change_users_login не может выполняться в определяемой пользователем транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner. Только члены предопределенной роли сервера sysadmin могут указывать параметр **Auto_Fix** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-showing-a-report-of-the-current-user-to-login-mappings"></a>A. Отображение отчета по текущим сопоставлениям пользователей именам входа  
 Следующий пример производит отчет по пользователям в текущей базе данных и их идентификаторам защиты (SIDs).  
  
```  
EXEC sp_change_users_login 'Report';  
```  
  
### <a name="b-mapping-a-database-user-to-a-new-sql-server-login"></a>Б. Сопоставление пользователя базы данных новому имени входа SQL Server  
 В следующем примере пользователь базы данных будет связан с новым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользователь базы данных `MB-Sales`, который сначала был сопоставлен с другим именем входа, будет повторно сопоставлен с именем входа `MaryB`.  
  
```  
--Create the new login.  
CREATE LOGIN MaryB WITH PASSWORD = '982734snfdHHkjj3';  
GO  
--Map database user MB-Sales to login MaryB.  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Update_One', 'MB-Sales', 'MaryB';  
GO  
```  
  
### <a name="c-automatically-mapping-a-user-to-a-login-creating-a-new-login-if-it-is-required"></a>В. Автоматическое сопоставление пользователя имени входа (создание при необходимости нового имени входа)  
 Следующий пример показывает, как использовать параметр `Auto_Fix`, чтобы сопоставить существующего пользователя с именем входа с таким же именем или создать имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`Mary`, которое имеет пароль `B3r12-3x$098f6`, если имя входа `Mary` не существует.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Auto_Fix', 'Mary', NULL, 'B3r12-3x$098f6';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_helplogins &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
