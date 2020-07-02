---
title: sp_setapprole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/12/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ba0a1d118ce62912e082b0553f000018e5d8233e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783718"
---
# <a name="sp_setapprole-transact-sql"></a>sp_setapprole (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Активирует разрешения, связанные с ролью приложения в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  

```sql
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```

## <a name="arguments"></a>Аргументы

`[ @rolename = ] 'role'`Имя роли приложения, определенной в текущей базе данных. Аргумент *Role* имеет тип **sysname**и не имеет значения по умолчанию. *роль* должна существовать в текущей базе данных.  
  
`[ @password = ] { encrypt N'password' }`Пароль, необходимый для активации роли приложения. Аргумент *Password* имеет тип **sysname**и не имеет значения по умолчанию. *пароль* может быть замаскирован с помощью функции **шифрования** ODBC. При использовании функции **Encrypt** пароль необходимо преобразовать в строку в Юникоде, поместив **N** перед первой кавычкой.  
  
 Параметр Encrypt не поддерживается для соединений, использующих **SqlClient**.  
  
> [!IMPORTANT]  
> Функция **шифрования** ODBC не обеспечивает шифрование. Не следует полагаться на эту функцию для защиты паролей, передаваемых по сети. Если эта информация будет передаваться по сети, используйте TLS или IPSec.
  
 **@encrypt= "нет"**  
 Указывает, что кодирование пароля не используется. Пароль передается серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как обычный текст. Это значение по умолчанию.  
  
 **@encrypt= ' ODBC '**  
 Указывает, что ODBC будет маскировать пароль с помощью функции **шифрования** ODBC перед отправкой пароля в [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Этот аргумент может быть указан, только если используется клиент ODBC или поставщик OLE DB для SQL Server.  
  
`[ @fCreateCookie = ] true | false`Указывает, следует ли создавать файл cookie. **значение true** неявно преобразуется в 1. **значение false** неявно преобразуется в 0.  
  
`[ @cookie = ] @cookie OUTPUT`Указывает выходной параметр, в котором будет содержаться файл cookie. Файл cookie создается только в том случае, если значение ** \@ фкреатекукие** равно **true**. **varbinary(8000)**  
  
> [!NOTE]  
> Параметр **OUTPUT** куки-файла для инструкции **sp_setapprole** в настоящее время описан в документации как **varbinary(8000)** , что верно определяет его максимальную длину. Однако текущая реализация возвращает параметр **varbinary(50)** . Приложения должны продолжать зарезервировать **varbinary (8000)** , чтобы приложение продолжало работать правильно, если размер возвращаемого файла cookie увеличивается в будущем выпуске.
  
## <a name="return-code-values"></a>Значения кода возврата

 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания

 После активации роли приложения с помощью **sp_setapprole**роль остается активной до тех пор, пока пользователь не отключится от сервера или не выполнит **sp_unsetapprole**. **sp_setapprole** могут выполняться только прямыми [!INCLUDE[tsql](../../includes/tsql-md.md)] операторами. **sp_setapprole** не может выполняться в другой хранимой процедуре или в пользовательской транзакции.  
  
 Общие сведения о ролях приложений см. в разделе [роли приложений](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
> Чтобы защитить пароль роли приложения при передаче по сети, следует всегда использовать зашифрованное соединение при включении роли приложения.
> [!INCLUDE[msCoName](../../includes/msconame-md.md)]Параметр **шифрования** ODBC не поддерживается **SqlClient**. Если необходимо сохранить учетные данные, зашифруйте их с помощью функций API. *Пароль* параметра хранится в виде одностороннего хэша. Чтобы сохранить совместимость с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , политика сложности паролей не применяется **sp_addapprole**. Чтобы применить политику сложности паролей, используйте параметр [создать роль приложения](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения

Требуется членство в **общедоступной** версии и знание пароля для роли.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. Включение роли приложения без параметра шифрования

 В следующем примере включается роль приложения с именем `SalesAppRole` с паролем в виде простого текста `AsDeF00MbXX`, созданная с разрешениями, специально предназначенными для приложения, выполняемого текущим пользователем.

```sql
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO
```

### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>Б. Включение роли приложения с куки-файлом и последующим возвратом к исходному контексту

 В следующем примере включается роль приложения `Sales11` с паролем `fdsd896#gfdbfdkjgh700mM` и создается куки-файл. В примере возвращается имя текущего пользователя, после чего происходит возврат к исходному контексту с помощью выполнения процедуры `sp_unsetapprole`.  

```sql
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.
GO
```

## <a name="see-also"></a>См. также

 [Системные хранимые процедуры &#40;хранимые процедуры Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) [безопасности &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) [Создание роли приложения &#40;TRANSACT-sql&#41;](../../t-sql/statements/create-application-role-transact-sql.md) [Удаление роли приложения &#40;Transact](../../t-sql/statements/drop-application-role-transact-sql.md) -SQL&#41;[sp_unsetapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)
