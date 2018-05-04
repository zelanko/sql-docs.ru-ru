---
title: sp_setapprole (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8dedeb6ee75c77ac3a887c37fb65ef128faa6c2e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Активирует разрешения, связанные с ролью приложения в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }   
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rolename =** ] **"***роль***"**  
 Имя роли приложения, определенной в текущей базе данных. *Роль* — **sysname**, не имеет значения по умолчанию. *роль* должен существовать в текущей базе данных.  
  
 [  **@password =** ] **{шифрования N'***пароль***"}**  
 Пароль, который требуется для активации роли приложения. *пароль* — **sysname**, не имеет значения по умолчанию. *пароль* может быть закодирован при помощи функции ODBC **шифрования** функции. При использовании **шифрования** функции, пароль должен быть преобразован в строку Юникода, поместив **N** перед первой кавычкой.  
  
 Параметр шифрования не поддерживается для подключений, использующих **SqlClient**.  
  
> [!IMPORTANT]  
>  ODBC **шифрования** функция не обеспечивает шифрование. Не следует полагаться на эту функцию для защиты паролей, передаваемых по сети. При передаче таких данных по сети используйте протокол SSL или IPSec.  
  
 **@encrypt = «none»**  
 Указывает, что кодирование пароля не используется. Пароль передается серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как обычный текст. Это значение по умолчанию.  
  
 **@encrypt= «odbc»**  
 Указывает, что ODBC закодирует пароль при помощи функции ODBC **шифрования** функция перед отправкой [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Этот аргумент может быть указан, только если используется клиент ODBC или поставщик OLE DB для SQL Server.  
  
 [  **@fCreateCookie =** ] **true** | **false**  
 Указывает, должен ли создаваться куки-файл. **значение true,** неявно преобразуется в 1. **false** неявно преобразуется в 0.  
  
 [  **@cookie =** ]  **@cookie ВЫХОДНЫХ ДАННЫХ**  
 Указывает выходной параметр, содержащий куки-файл. Куки-файл формируется только в том случае, если значение **@fCreateCookie** — **true**. **varbinary(8000)**  
  
> [!NOTE]  
>  Параметр **OUTPUT** куки-файла для инструкции **sp_setapprole** в настоящее время описан в документации как **varbinary(8000)** , что верно определяет его максимальную длину. Однако текущая реализация возвращает параметр **varbinary(50)**. Приложения должны продолжать зарезервировать **varbinary(8000)** , чтобы приложение продолжает работать неправильно, если в будущем выпуске увеличения размера возвращаемых куки-файлов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 После применения активации роли с помощью **sp_setapprole**, роль остается активной, пока пользователь отключается от сервера или выполняет **sp_unsetapprole**. **sp_setapprole** может быть запущена только непосредственными [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции. **sp_setapprole** не может быть выполнена внутри другой хранимой процедуры или внутри пользовательской транзакции.  
  
 Обзор ролей приложения см. в разделе [ролей приложения](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
>  Чтобы защитить пароля роли приложения в момент передачи по сети, необходимо всегда использовать зашифрованное соединение при включении роли приложения.  
>   
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC **шифрования** параметр не поддерживается в **SqlClient**. Если необходимо сохранить учетные данные, зашифруйте их с помощью функций API. Параметр *пароль* хранится в виде одностороннего хэша. Для сохранения совместимости с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не применяется политика сложности паролей **sp_addapprole**. Для принудительного применения политики сложности паролей, использовать [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **открытый** и знания пароля для роли.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. Включение роли приложения без параметра шифрования  
 В следующем примере включается роль приложения с именем `SalesAppRole` с паролем в виде простого текста `AsDeF00MbXX`, созданная с разрешениями, специально предназначенными для приложения, выполняемого текущим пользователем.  
  
```  
EXEC sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO  
```  
  
### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>Б. Включение роли приложения с куки-файлом и последующим возвратом к исходному контексту  
 В следующем примере включается роль приложения `Sales11` с паролем `fdsd896#gfdbfdkjgh700mM` и создается куки-файл. В примере возвращается имя текущего пользователя, после чего происходит возврат к исходному контексту с помощью выполнения процедуры `sp_unsetapprole`.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_unsetapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)  
  
  
