---
title: "Создание учетных данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 556fa0262696075d63ee549730f2d9824c482dd4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-credential-transact-sql"></a>CREATE CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает учетные данные уровня сервера. Учетные данные являются записью, которая содержит данные для проверки подлинности, необходимые для подключения к ресурсу вне SQL Server. Большинство учетных данных включают имя пользователя и пароль Windows. Например сохранение в нужное расположение резервной копии базы данных может потребоваться SQL Server для предоставления специальных учетных данных для доступа к этому расположению. Дополнительные сведения см. в разделе [учетные данные (компонент Database Engine)](../../relational-databases/security/authentication-access/credentials-database-engine.md).
  
> [!NOTE]  
>  Чтобы сделать учетные данные на уровне базы данных используют [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). Используйте учетные данные уровня сервера, если необходимо использовать те же учетные данные для нескольких баз данных на сервере. Используйте учетные данные уровня базы данных для обеспечения более переносимой базы данных. При перемещении базы данных на новом сервере, учетные данные уровня базы данных перемещаются вместе с его. Учетные данные уровня базы данных для использования на [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
        [ FOR CRYPTOGRAPHIC PROVIDER cryptographic_provider_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Указывает имя создаваемых учетных данных. *credential_name* не может начинаться со знака номера (#). Системные учетные данные начинаются с символов ##.  При использовании подписи общего доступа (SAS), это имя должно соответствовать путь к контейнеру, начинаться с https и не должен содержать косую черту. См. пример ниже D.  
  
 УДОСТОВЕРЕНИЕ **= "***identity_name***"**  
 Указывает имя учетной записи для использования при подключении за пределами сервера. При использовании учетных данных для доступа к хранилищу ключей Azure, **УДОСТОВЕРЕНИЕ** имя хранилища ключей. См. пример В далее. Когда для учетных данных используется подпись общего доступа (SAS), **УДОСТОВЕРЕНИЕ** — *подпись общего доступа*. См. пример ниже D.  
  
 СЕКРЕТ **= "***секрет***"**  
 Указывает секретный код, необходимый для исходящей проверки подлинности.  
  
 При использовании учетных данных для доступа к хранилищу ключей Azure **СЕКРЕТ** аргумент **CREATE CREDENTIAL** требует  *\<идентификатор клиента >* (без дефисов) и  *\<секрет >* из **участника-службы** в Azure Active Directory будут передаваться вместе без пробела между ними. См. пример В далее. Использование подписанного URL-адреса, учетные данные **СЕКРЕТ** токен подписи общего доступа. См. пример ниже D.  Сведения о создании хранимой политики доступа и подписанный URL-адрес для контейнера Azure см. в разделе [занятия 1: Создание хранимой политики доступа и подписанный URL-адрес для контейнера Azure](../../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
 ДЛЯ ПОСТАВЩИКА служб ШИФРОВАНИЯ *cryptographic_provider_name*  
 Указывает имя *поставщика управления ключами (EKM)*. Дополнительные сведения об управлении ключами см. в разделе [расширенного управления ключами &#40; Расширенное управление Ключами &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Замечания  

 Если IDENTITY является пользователем Windows, секретный код может быть паролем. Секретный код шифруется главным ключом службы. Если главный ключ службы формируется повторно, секретный код повторно шифруется, используя новый главный ключ службы.  
  
 После создания учетных данных, можно сопоставить их [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа с помощью [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) или [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md). Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа может быть сопоставлен только один набор учетных данных, но одни учетные данные могут соответствовать нескольким [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имена входа. Дополнительные сведения см. в разделе [учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Учетные данные уровня сервера могут сопоставляться только с входным именем, а не к пользователю базы данных. 
  
 Сведения об учетных данных отображается в [sys.credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) представления каталога.  
  
 При отсутствии учетных данных для поставщика, сопоставленных с именем входа, используются учетные данные, сопоставленные с учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Имени входа может быть сопоставлено несколько учетных данных, если они используются для отдельных поставщиков. У каждого поставщика должен быть только один набор учетных данных, сопоставленных одному имени входа. Одни и те же учетные данные могут быть сопоставлены нескольким именам входа.  
  
## <a name="permissions"></a>Permissions  
 Требуется **ALTER ANY CREDENTIAL** разрешение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-basic-example"></a>A. Базовый пример  
 Следующий пример создает учетные данные с именем `AlterEgo`. В эти учетные данные входят имя пользователя Windows `Mary5` и пароль.  
  
```  
CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-credential-for-ekm"></a>Б. Создание учетных данных для расширенного управления ключами  
 В следующем примере используется учетная запись с именем `User1OnEKM`, ранее созданная в модуле поставщика расширенного управления ключами с помощью средств управления поставщика, с основным типом учетной записи и паролем. **Sysadmin** учетную запись на сервере создает учетные данные, используемые для подключения к учетной записи расширенного управления Ключами и присваивает его `User1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи:  
  
```  
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
 В следующем примере создается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетные данные для [!INCLUDE[ssDE](../../includes/ssde-md.md)] для использования при доступе к хранилищу ключей Azure с использованием **соединитель SQL Server для хранилища ключей Microsoft Azure**. Полный пример использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соединителя. в разделе [расширенное управление ключами с помощью ключа хранилища Azure &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
> [!IMPORTANT]  
>  В аргументе **IDENTITY** **CREATE CREDENTIAL** необходимо указать имя хранилища ключей. **СЕКРЕТ** аргумент **CREATE CREDENTIAL** требует  *\<идентификатор клиента >* (без дефисов) и  *\<секрет >*  передаваемые друг с другом без пробела между ними.  
  
 В следующем примере из **идентификатора клиента** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) удаляются дефисы. Идентификатор клиента вводится как строка `EF5C8E094D2A4A769998D93440D8115D` , а **секрет** представляется строкой *SECRET_DBEngine*.  
  
```  
USE master;  
CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault',   
    SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
```  
  
 В следующем примере создается те же учетные данные, используя переменные для **идентификатор клиента** и **секрет** строк, которые затем соединяются для получения **СЕКРЕТ** аргумент. **Заменить** функция используется для удаления дефисов из идентификатора клиента.  
  
```  
DECLARE @AuthClientId uniqueidentifier = 'EF5C8E09-4D2A-4A76-9998-D93440D8115D';  
DECLARE @AuthClientSecret varchar(200) = 'SECRET_DBEngine';  
DECLARE @pwd varchar(max) = REPLACE(CONVERT(varchar(36), @AuthClientId) , '-', '') + @AuthClientSecret;  
  
EXEC ('CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault', SECRET = ''' + @PWD + '''   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;');  
```  
  
### <a name="d-creating-a-credential-using-a-sas-token"></a>Г. Создание учетных данных с помощью токена SAS  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
 Следующий пример создает учетные данные подписи общего доступа с помощью токена SAS.  Учебник по созданию хранимой политики доступа и подписанный URL-адрес для контейнера Azure и последующего создания учетных данных, с помощью подписи общего доступа см. в разделе [учебника: использование службы хранилища больших двоичных объектов Microsoft Azure с SQL Server 2016 базы данных](Tutorial:%20Using%20the%20Microsoft%20Azure%20Blob%20storage%20service%20with%20SQL%20Server%202016%20databases.md).  
  
> [!IMPORTANT]  
>  **Имя учетных данных** аргумент требует, что имя соответствует пути контейнера, начинаться с https и не содержат завершающую косую черту. **УДОСТОВЕРЕНИЕ** аргумент требует имя, *ПОДПИСИ общего доступа*. **СЕКРЕТ** аргумент требует маркер подписи общего доступа.  
  
```  
USE master  
CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a trailing forward slash.  
   WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
   , SECRET = 'sharedaccesssignature' –- this is the shared access signature token   
GO    
```  
  
## <a name="see-also"></a>См. также:  
 [Учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [Создание учетных данных области базы данных &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Занятие 2: Создание учетных данных SQL Server с помощью подписанного URL-адреса](../../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)   
 [Подписи коллективного доступа](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
  
  

