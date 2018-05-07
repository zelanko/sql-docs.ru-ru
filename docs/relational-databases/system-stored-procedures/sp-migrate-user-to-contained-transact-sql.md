---
title: sp_migrate_user_to_contained (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_migrate_user_to_contained
- sp_migrate_user_to_contained_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_migrate_user_to_contained
ms.assetid: b3a49ff6-46ad-4ee7-b6fe-7e54213dc33e
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 606898bf92ff727cd3d48f49f7f352cf06e8f9fe
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spmigrateusertocontained-transact-sql"></a>sp_migrate_user_to_contained (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Преобразует пользователя базы данных, сопоставленного с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в пользователя автономной базы данных с паролем. В автономной базе данных эта процедура позволяет удалить зависимости от экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором установлена база данных. **sp_migrate_user_to_contained** отделяет пользователя от исходного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, чтобы параметры, такие как язык по умолчанию и пароль могут осуществляться отдельно для автономной базы данных. **sp_migrate_user_to_contained** можно применить перед переносом автономной базы данных другой экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Чтобы устранить зависимости от текущего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра имена входа.  
  
 **Примечание** Эта процедура используется только в автономной базе данных. Дополнительные сведения см. в разделе [Contained Databases](../../relational-databases/databases/contained-databases.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_migrate_user_to_contained [ @username = ] N'user' ,   
    [ @rename = ] { N'copy_login_name' | N'keep_name' } ,   
    [ @disablelogin = ] { N'disable_login' | N'do_not_disable_login' }   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@username =** ] **N'***пользователя***"**  
 Имя пользователя в текущей автономной базе данных, сопоставленное с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], прошедшим проверку подлинности. Значение равно **sysname**, значение по умолчанию **NULL**.  
  
 [ **@rename =** ] **N'***copy_login_name***"** | **N'***keep_name***"**  
 Когда на основе имени входа пользователя базы данных имеет другое имя, отличное от имени входа, используйте *keep_name* сохранить имя пользователя базы данных во время миграции. Используйте *copy_login_name* для создания нового пользователя автономной базы данных с именем входа в систему, а не пользователя. Если пользователь базы данных, созданный на основе имени входа, имеет имя, совпадающее с именем входа, то в обоих вариантах будет создан пользователь автономной базы данных без изменения имени.  
  
 [ **@disablelogin =** ] **N'***disable_login***"** | **N'***do_not_disable_login***"**  
 *disable_login* отключает имя входа в базе данных master. Подключаться, если имя входа отключено, необходимо указать имя автономной базы данных как **исходный каталог** как часть строки соединения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_migrate_user_to_contained** создается пользователь автономной базы данных с паролем, вне зависимости от свойств и разрешений для имени входа. Например, процедура завершится успешно, если имя входа отключено или если пользователь отклонил **CONNECT** разрешение в базу данных.  
  
 **sp_migrate_user_to_contained** имеет следующие ограничения.  
  
-   Имя пользователя не должно уже существовать в базе данных.  
  
-   Преобразование встроенных пользователей, таких как dbo и guest, невозможно.  
  
-   Пользователь не может указываться в **EXECUTE AS** предложения подписанной хранимой процедуры.  
  
-   Пользователь не может владеть хранимую процедуру, которая включает в себя **предложение EXECUTE AS OWNER** предложения.  
  
-   **sp_migrate_user_to_contained** не может использоваться в системной базе данных.  
  
## <a name="security"></a>безопасность  
 При миграции пользователей следите за тем, чтобы не отключить и не удалить все имена входа администраторов экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если удаляются все имена входа, в разделе [подключение к SQL Server при системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Если **BUILTIN\Administrators** входа отсутствует, администраторы могут выполнять подключения, запустив свое приложение с помощью **Запуск от имени администратора** параметр.  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение **CONTROL SERVER** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-migrating-a-single-user"></a>A. Перенос одного пользователя  
 В следующем примере производится миграция имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Barry` в пользователя автономной базы данных с паролем. В этом примере не изменяется имя пользователя и имя входа остается активным (включенным).  
  
```sql  
sp_migrate_user_to_contained   
@username = N'Barry',  
@rename = N'keep_name',  
@disablelogin = N'do_not_disable_login' ;  
  
```  
  
### <a name="b-migrating-all-database-users-with-logins-to-contained-database-users-without-logins"></a>Б. Преобразование всех пользователей базы данных с именами входа в пользователей автономной базы данных без имен входа  
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
  
## <a name="see-also"></a>См. также  
 [Migrate to a Partially Contained Database](../../relational-databases/databases/migrate-to-a-partially-contained-database.md)   
 [Автономные базы данных](../../relational-databases/databases/contained-databases.md)  
  
  
