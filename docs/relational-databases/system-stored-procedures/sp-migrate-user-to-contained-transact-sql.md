---
title: sp_migrate_user_to_contained (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/11/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_migrate_user_to_contained
- sp_migrate_user_to_contained_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_migrate_user_to_contained
ms.assetid: b3a49ff6-46ad-4ee7-b6fe-7e54213dc33e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5bcafb24313851f58fd18fc19ebabd0ee98f6dd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68022336"
---
# <a name="sp_migrate_user_to_contained-transact-sql"></a>sp_migrate_user_to_contained (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Преобразует пользователя базы данных, сопоставленного с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в пользователя автономной базы данных с паролем. В автономной базе данных эта процедура позволяет удалить зависимости от экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором установлена база данных. **sp_migrate_user_to_contained** отделяет пользователя от исходного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имени входа, поэтому для автономной базы данных можно отдельно администрировать такие параметры, как пароль и язык по умолчанию. **sp_migrate_user_to_contained** можно использовать перед перемещением автономной базы данных в другой экземпляр, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] чтобы исключить зависимости от текущих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имен входа.  
  
> [!NOTE]
> Будьте внимательны при использовании **sp_migrate_user_to_contained**, так как вы не сможете отменить этот результат. Эта процедура используется только в автономной базе данных. Дополнительные сведения см. в разделе [автономные базы данных](../../relational-databases/databases/contained-databases.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_migrate_user_to_contained [ @username = ] N'user' ,   
    [ @rename = ] { N'copy_login_name' | N'keep_name' } ,   
    [ @disablelogin = ] { N'disable_login' | N'do_not_disable_login' }   
```  
  
## <a name="arguments"></a>Аргументы  
 [**@username =** ] **N "***пользователь***"**  
 Имя пользователя в текущей автономной базе данных, сопоставленное с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], прошедшим проверку подлинности. Аргумент имеет тип **sysname**и значение по умолчанию **null**.  
  
 [**@rename =** ] **N '***copy_login_name***'** | **n '***keep_name***'**  
 Если пользователь базы данных, основанный на имени входа, имеет имя, отличное от имени входа, используйте *keep_name* , чтобы во время миграции имя пользователя базы данных сохранялось. Используйте *copy_login_name* , чтобы создать нового пользователя автономной базы данных с именем входа, а не пользователя. Если пользователь базы данных, созданный на основе имени входа, имеет имя, совпадающее с именем входа, то в обоих вариантах будет создан пользователь автономной базы данных без изменения имени.  
  
 [**@disablelogin =** ] **N '***disable_login***'** | **n '***do_not_disable_login***'**  
 *disable_login* отключает имя входа в базе данных master. Чтобы подключиться, если имя входа отключено, соединение должно предоставить имя автономной базы данных в качестве **первоначального каталога** в строке подключения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 **sp_migrate_user_to_contained** создает пользователя автономной базы данных с паролем независимо от свойств или разрешений имени входа. Например, процедура может быть выполнена, если имя входа отключено или если пользователю отказано **в** доступе к базе данных.  
  
 **sp_migrate_user_to_contained** имеет следующие ограничения.  
  
-   Имя пользователя не должно уже существовать в базе данных.  
  
-   Преобразование встроенных пользователей, таких как dbo и guest, невозможно.  
  
-   Пользователь не может быть указан в предложении **EXECUTE AS** подписанной хранимой процедуры.  
  
-   Пользователь не может владеть хранимой процедурой, включающей предложение **EXECUTE AS OWNER** .  
  
-   **sp_migrate_user_to_contained** нельзя использовать в системной базе данных.  
  
## <a name="security"></a>Безопасность  
 При миграции пользователей следите за тем, чтобы не отключить и не удалить все имена входа администраторов экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если все имена для входа удалены, см. раздел [Подключение к SQL Server при блокировке системных администраторов](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Если указано имя входа **Builtin** \ администраторы, то администратор может подключиться, запустив приложение с помощью команды **Запуск от имени администратора** .  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение **CONTROL SERVER** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-migrating-a-single-user"></a>A. Перенос одного пользователя  
 В следующем примере производится миграция имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`Barry` в пользователя автономной базы данных с паролем. В этом примере имя пользователя не изменяется, а для имени входа используется значение включено.  
  
```sql  
sp_migrate_user_to_contained   
@username = N'Barry',  
@rename = N'keep_name',  
@disablelogin = N'do_not_disable_login' ;  
  
```  
  
### <a name="b-migrating-all-database-users-with-logins-to-contained-database-users-without-logins"></a>Б) Преобразование всех пользователей базы данных с именами входа в пользователей автономной базы данных без имен входа  
 В следующем примере выполняется миграция всех пользователей, основанных на имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в пользователей автономной базы данных с паролями. Этот пример исключает имена входа, которые не были включены. Этот пример должен выполняться в автономной базе данных.  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Миграция в частично автономную базу данных](../../relational-databases/databases/migrate-to-a-partially-contained-database.md)   
 [Автономные базы данных](../../relational-databases/databases/contained-databases.md)  
  
  
