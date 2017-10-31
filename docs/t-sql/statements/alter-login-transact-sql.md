---
title: "Разрешение ALTER LOGIN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_LOGIN_TSQL
- ALTER LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER LOGIN statement
- change password
- mapping logins [SQL Server]
- logins [SQL Server], modifying
- passwords [SQL Server], modifying
- names [SQL Server], logins
- modifying login accounts
ms.assetid: e247b84e-c99e-4af8-8b50-57586e1cb1c5
caps.latest.revision: 68
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9dd47cb63c56dbbfb5f31ea3f7b2c8d4f45e9d73
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-login-transact-sql"></a>ALTER LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет свойства учетной записи входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    | <cryptographic_credential_option>  
    }   
[;]  
  
<status_option> ::=  
        ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD = 'password' | hashed_password HASHED  
    [   
      OLD_PASSWORD = 'oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }  
    | CREDENTIAL = credential_name  
    | NO CREDENTIAL  
  
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
  
<cryptographic_credentials_option> ::=   
    ADD CREDENTIAL credential_name  
  | DROP CREDENTIAL credential_name  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER LOGIN login_name   
  {   
      <status_option>   
    | WITH <set_option> [ ,.. .n ]   
  }   
[;]  
  
<status_option> ::=  
    ENABLE | DISABLE  
  
<set_option> ::=   
    PASSWORD ='password'   
    [  
      OLD_PASSWORD ='oldpassword'  
    ]   
    | NAME = login_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    }   
  
<status_option> ::=ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD ='password'   
    [   
      OLD_PASSWORD ='oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }   
      
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
```  
  
## <a name="arguments"></a>Аргументы  
 *login_name*  
 Указывает имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое необходимо изменить. Имена входа домена необходимо заключать в квадратные скобки в формате [домен\пользователь].  
  
 ENABLE | DISABLE  
 Включает или отключает данное имя входа. Отключение входа не влияет на поведение имен входа, которые уже подключены. (Используйте `KILL` инструкции для завершения существующих подключений.) Отключенные имена входа сохраняют свои разрешения и все еще могут быть олицетворены.  
  
 ПАРОЛЬ **= "***пароль***"**  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает пароль для имени входа, которое необходимо изменить. В паролях учитывается регистр символов.  
  
 Постоянно активных подключений к базе данных SQL требуется повторная авторизация (выполняется компонентом Database Engine) каждые 10 часов. Компонент Database Engine пытается повторная авторизация с использованием пароля изначально отправлено и вмешательство пользователя не требуется. Для повышения производительности при сбросе пароля в базе данных SQL, соединение не будет повторно пройти проверку подлинности, даже если сброс подключения из-за пулов соединений. Это отличается от поведения в локальной среде SQL Server. Если пароль был изменен с момента подключения изначально был авторизован, необходимо завершить соединения и установить новое соединение с помощью нового пароля. Пользователь с разрешением KILL DATABASE CONNECTION можно явно разрыва подключения к базе данных SQL с помощью команды KILL. Дополнительные сведения см. в разделе [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md).  
  
 ПАРОЛЬ  **=**  *hashed_password*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применимо только к ключевому слову HASHED. Указывает хэшированное значение пароля для создаваемого имени входа.  
  
> [!IMPORTANT]  
>  Если имя входа (или пользователь автономной базы данных) используется для подключения и выполняется проверка подлинности, данные идентификаторов имени входа при подключении помещаются в кэш. Для имени входа, использующегося при проверке подлинности Windows, сюда относятся данные о членстве в группах Windows. Идентификатор имени входа остается зарегистрированным на протяжении периода, в который поддерживается соединение. Для принудительного изменения идентификатора, например сброса пароля или изменения членства в группе Windows, имя входа необходимо использовать для выхода из центра проверки подлинности (Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), а затем повторно выполнить вход. Член предопределенной роли сервера **sysadmin** или любого имени входа с разрешением **ALTER ANY CONNECTION** может использовать команду **KILL** и принудительно разорвать подключение для выполнения повторного подключения с использованием имени входа. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] может повторно использовать сведения о соединении при открытии нескольких соединений в окнах обозревателя объектов и редактора запросов. Закройте все соединения для принудительного повторного подключения.  
  
 HASHED  
   
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, что пароль, введенный после аргумента PASSWORD, уже хэширован. Если этот параметр не выбран, то пароль хэшируется перед сохранением в базе данных. Этот параметр следует использовать только для синхронизации имен входа между двумя серверами. Не используйте параметр HASHED для плановой смены паролей.  
  
 OLD_PASSWORD **= "***старый_пароль***"**  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Текущий пароль имени входа, которому будет присвоен новый пароль. В паролях учитывается регистр символов.  
  
 MUST_CHANGE  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если данный параметр включен, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребует ввести новый пароль при первом использовании измененного имени входа.  
  
 DEFAULT_DATABASE  **=**  *базы данных*  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает базу данных по умолчанию, назначенную имени входа.  
  
 DEFAULT_LANGUAGE  **=**  *языка*  
 
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает язык по умолчанию, присвоенный имени входа. Язык по умолчанию для всех имен входа базы данных SQL является английский и не может быть изменено. Язык по умолчанию `sa` входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Linux, английский, но его можно изменить.  
  
 ИМЯ = *login_name*  
 Указывает новое имя для имени входа, которое необходимо переименовать. Если оно является именем входа Windows, то идентификатор безопасности участника Windows, соответствующий новому имени, должен совпадать с идентификатором безопасности, относящимся к имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Новое имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа не может содержать символ обратной косой черты (\\).  
  
 CHECK_EXPIRATION = {ON | **OFF** }  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, должна ли политика истечения срока действия паролей принудительно применяться к этому имени входа. Значение по умолчанию — OFF.  
  
 CHECK_POLICY  **=**  { **ON** | {OFF}  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, что политики паролей Windows компьютера, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должны принудительно применяться к этому имени входа. Значение по умолчанию — ON.  
  
 Учетные данные = *credential_name*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя учетных данных для сопоставления с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Учетные данные уже должны существовать на сервере. Дополнительные сведения см. [учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Учетные данные, не может быть сопоставлен имени входа sa.  
  
 NO CREDENTIAL  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Удаляет любые существующие сопоставления имени входа с учетными данными сервера. Дополнительные сведения см. [учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 UNLOCK  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, что заблокированное имя входа должно быть разблокировано.  
  
 ADD CREDENTIAL  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Добавляет к имени входа учетные данные поставщика расширенного управления ключами. Дополнительные сведения см. в разделе [расширенного управления ключами &#40; Расширенное управление Ключами &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 DROP CREDENTIAL  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Удаляет учетные данные поставщика расширенного управления ключами (EKM) из имени входа. Дополнительные сведения см. [расширенного управления ключами &#40; Расширенное управление Ключами &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Замечания  
 Если параметр CHECK_POLICY имеет значение ON, аргумент HASHED использовать нельзя.  
  
 При изменении значения CHECK_POLICY на ON происходит следующее.  
  
-   Журнал паролей инициализируется значением хэша текущего пароля.  
  
 При изменении CHECK_POLICY на OFF происходит следующее.  
  
-   Параметр CHECK_EXPIRATION также получает значение OFF.  
  
-   Журнал паролей очищается.  
  
-   Значение *lockout_time* сбрасывается.  
  
Если задан параметр MUST_CHANGE, то параметры CHECK_EXPIRATION и CHECK_POLICY должны иметь значение ON. В противном случае выполнение инструкции приведет к ошибке.  
  
Если значение параметра CHECK_POLICY установлено равным OFF, то параметр CHECK_EXPIRATION не может иметь значения ON. Выполнение инструкции ALTER LOGIN с таким сочетанием параметров завершится ошибкой.  
  
Нельзя использовать параметр ALTER_LOGIN с аргументом DISABLE для запрещения доступа группе Windows. Например, параметр ALTER_LOGIN [*домен\группа*] DISABLE вернет следующее сообщение об ошибке:  
  
 «Сообщение 15151, уровень 16, состояние 1, строка 1.  
  
 «Не удается изменить имя входа "*домен\группа*", так как он не существует или отсутствует разрешение.»  
  
 Это сделано намеренно.  
  
В [!INCLUDE[ssSDS](../../includes/sssds-md.md)], требуются данные входа для проверки подлинности подключения и правила брандмауэра уровня сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедитесь в том, что база данных имеет последнюю версию таблицы, имена входа, выполните [DBCC FLUSHAUTHCACHE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY LOGIN.  
  
 Если используется параметр CREDENTIAL, то также требуется разрешение ALTER ANY CREDENTIAL.  
  
 Если изменяемое имя входа является членом **sysadmin** предопределенной роли сервера или участник, разрешение CONTROL SERVER, также требуется разрешение CONTROL SERVER при вносит следующие изменения:  
  
-   Сброс пароля без указания старого.  
  
-   Включение параметров MUST_CHANGE, CHECK_POLICY или CHECK_EXPIRATION.  
  
-   Изменение имени входа.  
  
-   Включение или отключение имени входа.  
  
-   Сопоставление имени входа с другими учетными данными.  
  
 Участник может изменить пароль, язык по умолчанию и базу данных по умолчанию для своего имени входа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-enabling-a-disabled-login"></a>A. Включение отключенного имени входа  
 Следующий пример включает имя входа `Mary5`.  
  
```tsql  
ALTER LOGIN Mary5 ENABLE;  
```  
  
### <a name="b-changing-the-password-of-a-login"></a>Б. Изменение пароля для имени входа  
 В следующем примере пароль для имени входа `Mary5` изменяется на надежный пароль.  
  
```tsql  
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';  
```  
  
### <a name="c-changing-the-name-of-a-login"></a>В. Изменение имени входа  
 Следующий пример изменяет имя входа `Mary5` на `John2`.  
  
```tsql  
ALTER LOGIN Mary5 WITH NAME = John2;  
```  
  
### <a name="d-mapping-a-login-to-a-credential"></a>Г. Сопоставление имени входа с учетными данными  
 Следующий пример сопоставляет имя входа `John2` с учетными данными `Custodian04`.  
  
```tsql  
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;  
```  
  
### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>Д. Сопоставление имени входа с учетными данными расширенного управления ключами  
 В следующем примере имя входа `Mary5` сопоставляется с учетными данными `EKMProvider1`.  
  
 
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql  
ALTER LOGIN Mary5  
ADD CREDENTIAL EKMProvider1;  
GO  
```  
  
### <a name="f-unlocking-a-login"></a>Е. Разблокирование имени входа  
 Чтобы разблокировать имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните следующую инструкцию, заменив **** нужным паролем учетной записи.  
  
  
```tsql  
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;  

GO  
```  
  
 Чтобы разблокировать учетную запись без изменения пароля, отключите и снова включите политику проверки.  
  
```tsql  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;  
GO  
```  
  
### <a name="g-changing-the-password-of-a-login-using-hashed"></a>Ж. Изменение пароля для имени входа с помощью параметра HASHED  
 В следующем примере пароль имени входа `TestUser` изменяется на заранее хэшированное значение.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql  
ALTER LOGIN TestUser WITH   
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;  
GO  
```  
  
 
  
## <a name="see-also"></a>См. также:  
 [Учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [DROP LOGIN &#40; Transact-SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  



