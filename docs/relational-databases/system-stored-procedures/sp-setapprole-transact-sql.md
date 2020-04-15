---
title: sp_setapprole (Трансакт-СЗЛ) Документы Майкрософт
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
ms.openlocfilehash: b158c4571deadadeaee23ffa6e46eb48a8c8446e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299615"
---
# <a name="sp_setapprole-transact-sql"></a>sp_setapprole (Transact-SQL)

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

`[ @rolename = ] 'role'`Определяется ли название роли приложения в текущей базе данных. *роль* **sysname**, без по умолчанию. *роль* должна существовать в текущей базе данных.  
  
`[ @password = ] { encrypt N'password' }`Требуется пароль для активации роли приложения. *пароль* **sysname**, без по умолчанию. *пароль* может быть запутан с помощью функции **шифрования** ODBC. При использовании функции **шифрования** пароль должен быть преобразован в строку Unicode, поставив **N** перед первым знаком цитаты.  
  
 Опция шифрования не поддерживается на **соединениях, использующих SqlClient.**  
  
> [!IMPORTANT]  
> Функция **шифрования** ODBC не обеспечивает шифрование. Не следует полагаться на эту функцию для защиты паролей, передаваемых по сети. Если эта информация будет передана через сеть, используйте TLS или IPSec.
  
 **@encrypt"Нет"**  
 Указывает, что кодирование пароля не используется. Пароль передается серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как обычный текст. Это значение по умолчанию.  
  
 **@encrypt-одбб'**  
 Уточняется, что ODBC запутает пароль с помощью функции **шифрования** ODBC перед отправкой пароля в [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Этот аргумент может быть указан, только если используется клиент ODBC или поставщик OLE DB для SQL Server.  
  
`[ @fCreateCookie = ] true | false`Определяет, будет ли создано файл cookie. **истинное** неявно преобразуется в 1. **ложное** неявно преобразуется в 0.  
  
`[ @cookie = ] @cookie OUTPUT`Определяет параметр вывода для содержания файла cookie. Файлы cookie генерируются только в том случае, если значение ** \@fCreateCookie** **верно.** **varbinary(8000)**  
  
> [!NOTE]  
> Параметр **OUTPUT** куки-файла для инструкции **sp_setapprole** в настоящее время описан в документации как **varbinary(8000)** , что верно определяет его максимальную длину. Однако текущая реализация возвращает параметр **varbinary(50)**. Приложения должны продолжать резервировать **varbinary(8000),** так что приложение продолжает работать правильно, если размер возврата файлов cookie увеличивается в будущем выпуске.
  
## <a name="return-code-values"></a>Значения кода возврата

 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks

 После активации роли приложения с помощью **sp_setapprole**роль остается активной до тех пор, пока пользователь не отключится от сервера или не выполнит **sp_unsetapprole.** **sp_setapprole** может быть выполнена [!INCLUDE[tsql](../../includes/tsql-md.md)] только прямыми заявлениями. **sp_setapprole** не может быть выполнена в рамках другой сохраненной процедуры или в рамках транзакции, определяемой пользователем.  
  
 Для обзора ролей приложений [см.](../../relational-databases/security/authentication-access/application-roles.md)  
  
> [!IMPORTANT]  
> Для защиты ролевой роли приложения при его передаче через сеть необходимо всегда использовать зашифрованное соединение при включении роли приложения.
> Опция [!INCLUDE[msCoName](../../includes/msconame-md.md)] **шифрования** ODBC не поддерживается **SqlClient**. Если необходимо сохранить учетные данные, зашифруйте их с помощью функций API. Пароль *параметра* хранится в виде одностороннего хэша. Чтобы сохранить совместимость с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]более ранними версиями, политика сложности паролей не обеспечивается **sp_addapprole.** Для обеспечения соблюдения политики сложности паролей используйте [CREATE APPLICATION ROLE.](../../t-sql/statements/create-application-role-transact-sql.md)  
  
## <a name="permissions"></a>Разрешения

Требуется членство в **общественности** и знание пароля для роли.  
  
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

## <a name="see-also"></a>См. также:

 [Процедуры хранения системы &#40;процедуры](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) хранения&#41;[безопасности Transact-S'L &#40;Transact-S'L&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) [CREATE APPLICATION ROLE &#40;Transact-S'L&#41;](../../t-sql/statements/create-application-role-transact-sql.md) DROP APPLICATION ROLE &#40;[Transact-S'L&#41;](../../t-sql/statements/drop-application-role-transact-sql.md) sp_unsetapprole &#40;[Transact-S'L&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)
