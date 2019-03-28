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
manager: craigg
ms.openlocfilehash: c18aa6fefb23bb3d388069773aa1633c29859e90
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533536"
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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

`[ @rolename = ] 'role'` — Имя роли приложения, определенной в текущей базе данных. *роль* — **sysname**, не имеет значения по умолчанию. *роль* должен существовать в текущей базе данных.  
  
`[ @password = ] { encrypt N'password' }` — Пароль, необходимый для активации роли приложения. *пароль* — **sysname**, не имеет значения по умолчанию. *пароль* может быть закодирован с помощью ODBC **шифрования** функции. При использовании **шифрования** функции, пароль должен быть преобразован в строку Юникода, поместив **N** перед первой кавычкой.  
  
 Параметр шифрования не поддерживается на соединениях, использующих **SqlClient**.  
  
> [!IMPORTANT]  
> ODBC **шифрования** функция не обеспечивает шифрование. Не следует полагаться на эту функцию для защиты паролей, передаваемых по сети. При передаче таких данных по сети используйте протокол SSL или IPSec.
  
 **@encrypt = «none»**  
 Указывает, что кодирование пароля не используется. Пароль передается серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как обычный текст. Это значение по умолчанию.  
  
 **@encrypt= 'odbc'**  
 Указывает, что ODBC закодирует пароль с помощью ODBC **шифрования** функцию перед отправкой компоненту [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Этот аргумент может быть указан, только если используется клиент ODBC или поставщик OLE DB для SQL Server.  
  
`[ @fCreateCookie = ] true | false` Указывает, является ли файл cookie должен быть создан. **значение true,** неявно преобразуется в 1. **false** неявно преобразуется в 0.  
  
`[ @cookie = ] @cookie OUTPUT` Указывает выходной параметр, содержащий файл cookie. Куки-файл формируется только в том случае, если значение **@fCreateCookie** — **true**. **varbinary(8000)**  
  
> [!NOTE]  
> Параметр **OUTPUT** куки-файла для инструкции **sp_setapprole** в настоящее время описан в документации как **varbinary(8000)** , что верно определяет его максимальную длину. Однако текущая реализация возвращает параметр **varbinary(50)**. Приложения должны продолжать зарезервировать **varbinary(8000)** таким образом, приложение для правильной работы в случае увеличения размера куки в будущем выпуске.
  
## <a name="return-code-values"></a>Значения кода возврата

 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания

 После приложение активации роли с помощью **sp_setapprole**, роль остается активной, пока пользователь отключается от сервера или выполняет **sp_unsetapprole**. **sp_setapprole** может быть запущена только непосредственными [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций. **sp_setapprole** не может быть выполнена внутри другой хранимой процедуры или определяемой пользователем транзакции.  
  
 Обзор ролей приложения, см. в разделе [ролей приложения](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
> Чтобы защитить пароля роли приложения, при передаче по сети, следует всегда использовать зашифрованное соединение при включении роли приложения.
> [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC **шифрования** параметр не поддерживается **SqlClient**. Если необходимо сохранить учетные данные, зашифруйте их с помощью функций API. Параметр *пароль* хранится в виде одностороннего хэша. Для сохранения совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], политика сложности паролей не применяется принудительно **sp_addapprole**. Чтобы требовать использование политики сложности паролей, используйте [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения

Требуется членство в **открытый** и знания пароля для роли.  
  
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

 [Системные хранимые процедуры &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) [хранимые процедуры безопасности &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) [CREATE APPLICATION ROLE &#40;Transact-SQL&#41; ](../../t-sql/statements/create-application-role-transact-sql.md) [DROP APPLICATION ROLE &#40;Transact-SQL&#41; ](../../t-sql/statements/drop-application-role-transact-sql.md) [sp_unsetapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)
