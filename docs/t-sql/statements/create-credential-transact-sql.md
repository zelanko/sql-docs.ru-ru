---
title: CREATE CREDENTIAL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/25/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREDENTIAL_TSQL
- SQL13.SWB.CREDENTIAL.GENERAL.F1
- CREATE CREDENTIAL
- CREATE_CREDENTIAL_TSQL
- CREDENTIAL
dev_langs:
- TSQL
helpviewer_keywords:
- SECRET clause
- authentication [SQL Server], credentials
- CREATE CREDENTIAL statement
- credentials [SQL Server], CREATE CREDENTIAL statement
ms.assetid: d5e9ae69-41d9-4e46-b13d-404b88a32d9d
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 35db04fee2cc8d17034414bce9c994db501d5c02
ms.sourcegitcommit: 445842da7c7d216b94a9576e382164c67f54e19a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2019
ms.locfileid: "71680897"
---
# <a name="create-credential-transact-sql"></a>CREATE CREDENTIAL (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

Создает учетные данные на уровне сервера. Учетные данные являются записью, которая содержит сведения для проверки подлинности, необходимые для подключения к ресурсу извне SQL Server. Большинство учетных данных включают имя пользователя и пароль Windows. Например, при сохранении резервной копии базы данных в определенном расположении серверу SQL Server может потребоваться предоставить специальные учетные данные для доступа к этому расположению. Дополнительные сведения см. в статье [Учетные данные (компонент Database Engine)](../../relational-databases/security/authentication-access/credentials-database-engine.md).

> [!NOTE]
> Чтобы создать учетные данные на уровне базы данных, используйте инструкцию [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). Учетные данные на уровне сервера следует применять тогда, когда для доступа к нескольким базам данных на сервере необходимо использовать одни и те же учетные данные. Учетные данные на уровне базы данных повышают ее переносимость. При переносе базы данных на новый сервер учетные данные на уровне базе данных переносятся вместе с ней. Используйте учетные данные на уровне базы данных в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```
CREATE CREDENTIAL credential_name
WITH IDENTITY = 'identity_name'
    [ , SECRET = 'secret' ]
        [ FOR CRYPTOGRAPHIC PROVIDER cryptographic_provider_name ]
```

## <a name="arguments"></a>Аргументы

*credential_name*. Указывает имя создаваемых учетных данных. Аргумент *credential_name* не может начинаться с символа номера (#). Системные учетные данные начинаются с символов ##. 

> [!IMPORTANT]
> При использовании подписанного URL-адреса (SAS) это имя должно соответствовать пути к контейнеру, начинаться с префикса https и не должно содержать косой черты. См. [пример Г](#d-creating-a-credential-using-a-sas-token).

IDENTITY **='** _identity\_name_ **'** . Указывает имя учетной записи для использования при подключении за пределами сервера. При использовании учетных данных для доступа к хранилищу Azure Key Vault **IDENTITY** — это имя хранилища ключей. См. пример В далее. Если в учетных данных используется подписанный URL-адрес (SAS), **IDENTITY** имеет значение *SHARED ACCESS SIGNATURE*. См. пример Г ниже.

> [!IMPORTANT]
> База данных SQL Azure поддерживает только удостоверения Azure Key Vault и удостоверения на основе подписанного URL-адреса. Удостоверения пользователей Windows не поддерживаются.

SECRET **='** _secret_ **'** . Указывает секретный код, необходимый для исходящей проверки подлинности.

При использовании учетных данных для доступа к хранилищу Azure Key Vault в аргументе **SECRET** инструкции **CREATE CREDENTIAL** требуется указать *\<идентификатор клиента>* (без дефисов) и *\<секрет>* **субъекта-службы** в Azure Active Directory без пробела между ними. См. пример В далее. Если в учетных данных используется подписанный URL-адрес, **SECRET** — это токен подписанного URL-адреса. См. пример Г ниже. Для получения дополнительных сведений см. [Занятие 1. Создание хранимой политики доступа и подписанного URL-адреса для контейнера Azure](../../relational-databases/tutorial-use-azure-blob-storage-service-with-sql-server-2016.md#1---create-stored-access-policy-and-shared-access-storage).

FOR CRYPTOGRAPHIC PROVIDER *cryptographic_provider_name*. Указывает имя *поставщика управления ключами Enterprise (EKM)* . Дополнительные сведения об управлении ключами см. в статье [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).

## <a name="remarks"></a>Remarks

Если IDENTITY является пользователем Windows, секретный код может быть паролем. Секретный код шифруется главным ключом службы. Если главный ключ службы формируется повторно, секретный код повторно шифруется, используя новый главный ключ службы.

После создания учетных данных можно сопоставить их с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используя инструкцию [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) или [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md). Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть сопоставлено только с одними учетными данными, но одни учетные данные могут быть сопоставлены с несколькими именами входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md). Учетные данные уровня сервера можно сопоставить только с именем для входа, но не с пользователем базы данных. 

Сведения об учетных данных отображаются в представлении каталога [sys.credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md).

При отсутствии учетных данных для поставщика, сопоставленных с именем входа, используются учетные данные, сопоставленные с учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Имени входа может быть сопоставлено несколько учетных данных, если они используются для отдельных поставщиков. У каждого поставщика должен быть только один набор учетных данных, сопоставленных одному имени входа. Одни и те же учетные данные могут быть сопоставлены нескольким именам входа.

## <a name="permissions"></a>Разрешения

Требуется разрешение **ALTER ANY CREDENTIAL**.

## <a name="examples"></a>Примеры

### <a name="a-basic-example"></a>A. Базовый пример

Следующий пример создает учетные данные с именем `AlterEgo`. В эти учетные данные входят имя пользователя Windows `Mary5` и пароль.

```sql
CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',
    SECRET = '<EnterStrongPasswordHere>';
GO
```

### <a name="b-creating-a-credential-for-ekm"></a>Б. Создание учетных данных для расширенного управления ключами

В следующем примере используется учетная запись с именем `User1OnEKM`, ранее созданная в модуле поставщика расширенного управления ключами с помощью средств управления поставщика, с основным типом учетной записи и паролем. Учетная запись **sysadmin** на сервере создает учетные данные, которые используются для соединения с учетной записью поставщика расширенного управления ключами, и назначает их учетной записи `User1`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:

```sql
CREATE CREDENTIAL CredentialForEKM
    WITH IDENTITY='User1OnEKM', SECRET='<EnterStrongPasswordHere>'
    FOR CRYPTOGRAPHIC PROVIDER MyEKMProvider;
GO

/* Modify the login to assign the cryptographic provider credential */
ALTER LOGIN Login1
ADD CREDENTIAL CredentialForEKM;

/* Modify the login to assign a non cryptographic provider credential */
ALTER LOGIN Login1
WITH CREDENTIAL = AlterEgo;
GO
```

### <a name="c-creating-a-credential-for-ekm-using-the-azure-key-vault"></a>В. Создание учетных данных для расширенного управления ключами с помощью хранилища ключей Azure

В приведенном ниже примере создаются учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует при доступе к хранилищу Azure Key Vault с помощью **Соединителя SQL Server для Microsoft Azure Key Vault**. Полный пример использования соединителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).

> [!IMPORTANT]
> В аргументе **IDENTITY** **CREATE CREDENTIAL** необходимо указать имя хранилища ключей. Для аргумента **SECRET** инструкции **CREATE CREDENTIAL** необходимо передать *\<Код клиента>* (без дефисов) и *\<Секрет>* , не разделенные пробелом.

 В следующем примере из **идентификатора клиента** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) удаляются дефисы. Идентификатор клиента вводится как строка `EF5C8E094D2A4A769998D93440D8115D` , а **секрет** представляется строкой *SECRET_DBEngine*.

```sql
USE master;
CREATE CREDENTIAL Azure_EKM_TDE_cred
    WITH IDENTITY = 'ContosoKeyVault',
    SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;
```

В приведенном ниже примере создаются те же учетные данные с использованием переменных для строк **Идентификатор клиента** и **Секрет**, которые затем сцепляются для получения аргумента **SECRET**. Функция **REPLACE** используется для удаления дефисов из идентификатора клиента.

```sql
DECLARE @AuthClientId uniqueidentifier = 'EF5C8E09-4D2A-4A76-9998-D93440D8115D';
DECLARE @AuthClientSecret varchar(200) = 'SECRET_DBEngine';
DECLARE @pwd varchar(max) = REPLACE(CONVERT(varchar(36), @AuthClientId) , '-', '') + @AuthClientSecret;

EXEC ('CREATE CREDENTIAL Azure_EKM_TDE_cred
    WITH IDENTITY = 'ContosoKeyVault', SECRET = ''' + @PWD + '''
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;');
```

### <a name="d-creating-a-credential-using-a-sas-token"></a>Г. Создание учетных данных с помощью токена SAS

**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]по [текущую версию](https://go.microsoft.com/fwlink/p/?LinkId=299658) и в управляемых экземплярах базы данных SQL Azure.

В приведенном ниже примере создаются учетные данные с подписанным URL-адресом с использованием токена SAS. См. дополнительные сведения о создании хранимой политики доступа и подписанного URL-адреса в контейнере Azure с последующим созданием учетных данных с помощью подписанного URL-адреса в [руководстве по использованию службы хранилища больших двоичных объектов Microsoft Azure с базами данных SQL Server 2016](../../relational-databases/tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).

> [!IMPORTANT]
> Аргумент **CREDENTIAL NAME** требует, чтобы имя соответствовало пути к контейнеру, начиналось с префикса https и не содержало завершающей косой черты. Для аргумента **IDENTITY** требуется имя *SHARED ACCESS SIGNATURE*. Для аргумента **SECRET** требуется токен подписанного URL-адреса.
>
> В начале секрета **SHARED ACCESS SIGNATURE** не должно быть символа **?** .

```sql
USE master
CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a trailing forward slash.
    WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.
    , SECRET = 'sharedaccesssignature' -- this is the shared access signature token
GO
```

## <a name="see-also"></a>См. также:

- [Учетные данные (компонент Database Engine)](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [ALTER CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-credential-transact-sql.md)
- [DROP CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-credential-transact-sql.md)
- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)
- [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)
- [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)
- [Занятие 2. Создание учетных данных SQL Server с помощью подписанного URL-адреса](../../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)
- [Подписанные URL-адреса](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/)
