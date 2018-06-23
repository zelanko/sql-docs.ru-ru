---
title: Расширенное управление ключами с помощью Azure Key Vault (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
caps.latest.revision: 37
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 41124ce445bf6f008c7aa473d12853a551aa36b2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194684"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a>Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Соединитель для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] хранилище ключей Azure позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] шифрования для использования службы хранилища ключей Azure в качестве [расширенного управления ключами &#40;расширенного управления Ключами&#41; ](extensible-key-management-ekm.md) поставщика для защиты его ключи шифрования.  
  
 Разделы данной темы  
  
-   [Использование расширенного управления Ключами](#Uses)  
  
-   [Шаг 1: Настройка хранилища ключей для использования в SQL Server](#Step1)  
  
-   [Шаг 2: Установка соединителя SQL Server](#Step2)  
  
-   [Шаг 3: Настройка SQL Server для использования поставщика расширенного управления Ключами для хранилища ключей](#Step3)  
  
-   [Пример а. прозрачное шифрование данных с помощью асимметричного ключа из хранилища ключей](#ExampleA)  
  
-   [Пример б. шифрование резервных копий с помощью асимметричного ключа из хранилища ключей](#ExampleB)  
  
-   [Пример в. шифрование на уровне столбца с помощью асимметричного ключа из хранилища ключей](#ExampleC)  
  
##  <a name="Uses"></a> Использование расширенного управления Ключами  
 Организация может использовать шифрование [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для защиты конфиденциальных данных. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включает шифрование [прозрачное шифрование данных &#40;TDE&#41;](transparent-data-encryption.md), [шифрование на уровне столбцов](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE) и [шифрование резервной копии](../../backup-restore/backup-encryption.md). Во всех этих случаях данные шифруются с помощью симметричного ключа шифрования. Симметричный ключ шифрования затем шифруется иерархией ключей, хранящихся в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Кроме того, архитектура поставщика EKM использует [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для защиты ключей шифрования данных с помощью асимметричного ключа хранится за пределами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] во внешнем поставщике служб шифрования. Архитектура поставщика EKM добавляет дополнительный уровень безопасности и позволяет организациям разделить управление ключами и данными.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Соединитель для хранилища ключей Azure позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать масштабируемую, высокопроизводительную и высокодоступную ключа службу хранилища в качестве поставщика расширенного управления Ключами для защиты ключа шифрования. Служба хранилища ключей можно использовать с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] установок на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] виртуальных машинах Azure и для локальных серверов. Служба хранилища ключей также предоставляет возможность использовать жестко контролируемые и отслеживаемые аппаратные модули безопасности (HSM) для обеспечения более высокого уровня защиты асимметричных ключей шифрования. Дополнительные сведения о хранилище ключей см. в статье [Хранилище ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521401).  
  
 На следующем изображении представлен поток процесса расширенного управления ключами с использованием хранилища ключей. Номера шагов процесса на изображении не обязательно соответствуют номерам шагов установки, указанным после изображения.  
  
 ![Расширенное управление ключами с помощью Azure Key Vault (SQL Server)](../../../database-engine/media/ekm-using-azure-key-vault.png "Расширенное управление ключами с помощью Azure Key Vault (SQL Server)")  
  
##  <a name="Step1"></a> Шаг 1: Настройка хранилища ключей для использования в SQL Server  
 Выполните следующие действия, чтобы настроить хранилище ключей для использования с [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] в целях защиты ключа шифрования. Организация может уже использовать хранилище. Если хранилище не существует, администратор Azure в вашей организации, назначенный для управления ключами шифрования создайте хранилище, создать асимметричный ключ в хранилище и затем авторизовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для использования ключа. Ознакомьтесь со службой хранилища ключей, изучив статью [Приступая к работе с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521402), и справочником по [командлетам PowerShell для работы с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521403) .  
  
> [!IMPORTANT]  
>  Если у вас несколько подписок Azure, необходимо использовать подписку, содержащую [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
1.  **Создание хранилища.** Создайте хранилище, следуя инструкциям в разделе **Создание хранилища ключей** статьи [Приступая к работе с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521402). Запишите имя хранилища. В этом разделе используется имя **ContosoKeyVault** .  
  
2.  **Создание асимметричного ключа в хранилище:** асимметричного ключа в хранилище ключей используется для защиты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ключей шифрования. Только открытая часть асимметричного ключа покидает хранилище, частная же область никогда не экспортируется. Все криптографические операции, использующие асимметричный ключ, делегируются в хранилище ключей Azure и защищаются системой безопасности хранилища.  
  
     Существует несколько способов создания асимметричного ключа и сохранения его в хранилище. Можно создать ключ извне и импортировать его в хранилище в виде PFX-файла. Или можно создать ключ непосредственно в хранилище с помощью API хранилища ключей.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Соединителю асимметричные ключи RSA 2048 бит и имя ключа можно использовать только символы «a-z», «A-Z», «0-9», и «-». В этом документе имя асимметричного ключа — **ContosoMasterKey**. Замените его на уникальное имя ключа.  
  
    > [!IMPORTANT]  
    >  Импорт асимметричного ключа настоятельно рекомендуется для рабочих сценариев, так как это позволяет администратору передать ключ в систему переноса ключей. Если в хранилище создается асимметричный ключ, он не может быть передан, так как закрытый ключ не может покидать хранилище. Ключи, используемые для защиты важных данных, должны быть перенесены. Потеря асимметричного ключа приведет к невозможности восстановить данные.  
  
    > [!IMPORTANT]  
    >  Хранилище ключей поддерживает несколько версий ключа с одним именем. Ключи, используемые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] соединитель не должно быть система управления версиями или откат. Если администратору требуется откатить ключ, используемый для шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , следует создать ключ с другим именем в хранилище и использовать его для шифрования ключа шифрования базы данных.  
  
     Дополнительные сведения о том, как импортировать ключ в хранилище ключей или создать ключ в хранилище ключей (не рекомендуется для рабочей среды), см. в разделе **Добавление ключа или секретного кода в хранилище ключей** статьи [Приступая к работе с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521402).  
  
3.  **Получение субъектов-служб Azure Active Directory для SQL Server.** Когда организация регистрируется в облачной службе Майкрософт, она получает Azure Active Directory. Создание **участников службы** в Azure Active Directory для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для использования (для проверки подлинности в Azure Active Directory) при доступе к хранилищу ключей.  
  
    -   Один **участника-службы** понадобится [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] администратора для доступа к хранилищу при настройке [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать шифрование.  
  
    -   Другой **участника-службы** понадобится [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] доступа к хранилищу для распаковки ключей, используемых в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] шифрования.  
  
     Дополнительные сведения о регистрации приложения и создании субъекта-службы см. в разделе **Регистрация приложения в Azure Active Directory** статьи [Приступая к работе с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521402). Процесс регистрации возвращает **идентификатор приложения** (также известный как **идентификатор клиента**) и **ключ проверки подлинности** (также известный как **секрет**) для каждого **субъекта-службы**Azure Active Directory. При использовании в `CREATE CREDENTIAL` инструкции дефис необходимо удалить из **идентификатор КЛИЕНТА**. Запишите их для использования в следующих скриптах.  
  
    -   **Субъект-служба** для имени входа **sysadmin** : **CLIENTID_sysadmin_login** и **SECRET_sysadmin_login**  
  
    -   **Субъект-служба** для [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** и **SECRET_DBEngine**.  
  
4.  **Предоставление субъекту-службе разрешений для доступа к хранилищу ключей.** Субъектам-службам **CLIENTID_sysadmin_login** и **CLIENTID_DBEngine** необходимы разрешения **get**, **list**, **wrapKey**, и **unwrapKey** в хранилище ключей. Если вы планируете создать ключи с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо предоставить **создания** разрешение в хранилище ключей.  
  
    > [!IMPORTANT]  
    >  У пользователей должны быть по крайней мере операции **wrapKey** и **unwrapKey** для хранилища ключей.  
  
     Дополнительные сведения о предоставлении разрешений в хранилище см. в разделе **Авторизация приложения для использования ключа или секрета** статьи [Приступая к работе с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521402).  
  
     Ссылки на документацию по хранилищу ключей Azure  
  
    -   [Что такое хранилище ключей Azure?](http://go.microsoft.com/fwlink/?LinkId=521401)  
  
    -   [Приступая к работе с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521402)  
  
    -   Справочник по [командлетам PowerShell для работы с хранилищем ключей Azure](http://go.microsoft.com/fwlink/?LinkId=521403)  
  
##  <a name="Step2"></a> Шаг 2: Установка соединителя SQL Server  
 Соединитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будет загружен и установлен администратором компьютера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Соединителя можно загрузить из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/p/?LinkId=521700).  Выполните поиск **соединителя SQL Server для хранилища ключей Microsoft Azure**, просмотрите подробные сведения, требования к системе и инструкции по установке, загрузите соединитель и начните установку с помощью команды **Выполнить**. Прочитайте лицензионное соглашение, примите его условия и продолжайте.  
  
 По умолчанию соединитель устанавливается в **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**. Эту папку можно изменить во время установки. (В этом случае измените и следующие скрипты.)  
  
 После завершения установки на компьютер установлены следующие компоненты.  
  
-   **Microsoft.AzureKeyVaultService.EKM.dll**: это поставщик служб шифрования расширенного управления Ключами DLL, должен быть зарегистрирован с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции CREATE CRYPTOGRAPHIC PROVIDER.  
  
-   **Соединитель SQL Server для хранилища ключей Azure**— это служба Windows, которая позволяет поставщику EKM взаимодействовать с хранилищем ключей.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Установки соединителя также позволяет при необходимости загрузить примеры скриптов для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] шифрования.  
  
##  <a name="Step3"></a> Шаг 3: Настройка SQL Server для использования поставщика расширенного управления Ключами для хранилища ключей  
  
###  <a name="Permissions"></a> Permissions  
 Для завершения всего процесса требуется разрешение CONTROL SERVER или членство в предопределенной роли сервера **sysadmin** . Для определенных действий необходимы следующие разрешения.  
  
-   Для создания поставщика служб шифрования требуется разрешение CONTROL SERVER или членство в предопределенной роли сервера **sysadmin** .  
  
-   Для изменения параметра конфигурации и выполнения инструкции RECONFIGURE должно быть предоставлено разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
-   Для создания учетных данных требуется разрешение ALTER ANY CREDENTIAL.  
  
-   Для добавления учетных данных необходимо разрешение ALTER ANY LOGIN.  
  
-   Для создания асимметричного ключа требуется разрешение CREATE ASYMMETRIC KEY.  
  
###  <a name="TsqlProcedure"></a> Чтобы настроить SQL Server для использования поставщика служб шифрования  
  
1.  Настройте [!INCLUDE[ssDE](../../../includes/ssde-md.md)] для использования EKM и зарегистрируйте (создайте) поставщика служб шифрования с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    ```  
    -- Enable advanced options.  
    USE master;  
    GO  
  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
  
    -- Create a cryptographic provider, using the SQL Server Connector  
    -- which is an EKM provider for the Azure Key Vault. This example uses   
    -- the name AzureKeyVault_EKM_Prov.  
  
    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO   
    ```  
  
2.  Программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] учетные данные для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] входа администратора для использования хранилище ключей для настройки и управления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сценариев шифрования.  
  
    > [!IMPORTANT]  
    >  **УДОСТОВЕРЕНИЕ** аргумент `CREATE CREDENTIAL` необходимо указать имя хранилища ключей. **СЕКРЕТ** аргумент `CREATE CREDENTIAL` требует  *\<идентификатор клиента >* (без дефисов) и  *\<секрет >* для передачи друг с другом без пробела между ними.  
  
     В следующем примере из **идентификатора клиента** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) удаляются дефисы. Идентификатор клиента вводится как строка `EF5C8E094D2A4A769998D93440D8115D` , а **секрет** представляется строкой *SECRET_sysadmin_login*.  
  
    ```  
    USE master;  
    CREATE CREDENTIAL sysadmin_ekm_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
  
    -- Add the credential to the SQL Server administrators domain login   
    ALTER LOGIN [<domain>/<login>]  
    ADD CREDENTIAL sysadmin_ekm_cred;  
    ```  
  
     Пример использования переменных для `CREATE CREDENTIAL` аргументы и программного удаления дефисов из идентификатора клиента см. в разделе [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).  
  
3.  Если вы импортировали асимметричный ключ, как описано выше в шаге 1 раздела 3, откройте ключ, указав имя ключа в следующем примере.  
  
    ```  
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',  
    CREATION_DISPOSITION = OPEN_EXISTING;  
    ```  
  
     Хотя это и не рекомендуется для рабочей среды (поскольку ключ невозможно экспортировать), можно создать асимметричный ключ напрямую в хранилище с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если вы не импортировали ключ ранее, создайте асимметричный ключ в хранилище для тестирования с помощью следующего скрипта. Выполните скрипт, используя имя входа, предоставленное в учетных данных **sysadmin_ekm_cred** .  
  
    ```  
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH ALGORITHM = RSA_2048,  
    PROVIDER_KEY_NAME = 'ContosoMasterKey';  
    ```  
  
> [!TIP]  
>  Пользователям, получившим ошибки **не удалось экспортировать открытый ключ от поставщика. Код ошибки поставщика: 2053.** следует проверить в хранилище ключей свои разрешения **get**, **list**, **wrapKey**и **unwrapKey** в хранилище ключей.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
## <a name="examples"></a>Примеры  
  
###  <a name="ExampleA"></a> Пример а. прозрачное шифрование данных с помощью асимметричного ключа из хранилища ключей  
 После выполнения действий, описанных выше, создайте учетные данные и имя входа, создайте ключ шифрования базы данных, защищенный асимметричным ключом, в хранилище ключей. Используйте ключ для шифрования базы данных с помощью TDE.  
  
 Для шифрования базы данных требуется разрешение CONTROL в базе данных.  
  
##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a>Включение прозрачного шифрования данных с помощью службы расширенного управления ключами и хранилища ключей  
  
1.  Создайте учетные данные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для [!INCLUDE[ssDE](../../../includes/ssde-md.md)], которые будут использоваться при доступе к EKM хранилища ключей во время загрузки базы данных.  
  
    > [!IMPORTANT]  
    >  **УДОСТОВЕРЕНИЕ** аргумент `CREATE CREDENTIAL` необходимо указать имя хранилища ключей. **СЕКРЕТ** аргумент `CREATE CREDENTIAL` требует  *\<идентификатор клиента >* (без дефисов) и  *\<секрет >* для передачи друг с другом без пробела между ними.  
  
     В следующем примере из **идентификатора клиента** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) удаляются дефисы. Идентификатор клиента вводится как строка `EF5C8E094D2A4A769998D93440D8115D` , а **секрет** представляется строкой *SECRET_DBEngine*.  
  
    ```  
    USE master;  
    CREATE CREDENTIAL Azure_EKM_TDE_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
    ```  
  
2.  Создайте имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которое будет использоваться [!INCLUDE[ssDE](../../../includes/ssde-md.md)] для прозрачного шифрования данных, и добавьте к нему учетные данные. В этом примере используется асимметричный ключ CONTOSO_KEY из хранилища ключей, который был импортирован или создан ранее для базы данных master, как описано в [шаге 3 раздела 3](#Step3) выше.  
  
    ```  
    USE master;  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it loads a database   
    -- encrypted by TDE.  
    CREATE LOGIN TDE_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY;  
    GO   
  
    -- Alter the TDE Login to add the credential for use by the   
    -- Database Engine to access the key vault  
    ALTER LOGIN TDE_Login   
    ADD CREDENTIAL Azure_EKM_TDE_cred ;  
    GO  
    ```  
  
3.  Создайте ключ шифрования базы данных (DEK), который будет использоваться для прозрачного шифрования данных. Ключ DEK можно создать, используя любой поддерживаемый алгоритм SQL Server или длину ключа. Ключ DEK будет защищен асимметричным ключом в хранилище ключей.  
  
     В этом примере используется асимметричный ключ CONTOSO_KEY из хранилища ключей, который был импортирован или создан ранее, как описано в [шаге 3 раздела 3](#Step3) выше.  
  
    ```  
    USE ContosoDatabase;  
    GO  
  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_128   
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE ContosoDatabase   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
     Дополнительные сведения см. в следующих разделах:  
  
    -   [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
    -   [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
###  <a name="ExampleB"></a> Пример б. шифрование резервных копий с помощью асимметричного ключа из хранилища ключей  
 Зашифрованные резервные копии поддерживаются начиная с [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. В следующем примере создается и восстанавливается резервная копия, зашифрованная ключом шифрования данных, который защищен асимметричным ключом в хранилище ключей.  
  
```  
USE master;  
BACKUP DATABASE [DATABASE_TO_BACKUP]  
TO DISK = N'[PATH TO BACKUP FILE]'   
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD,   
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);  
GO  
```  
  
 Образец кода восстановления.  
  
```  
RESTORE DATABASE [DATABASE_TO_BACKUP]  
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;  
GO  
```  
  
 Дополнительные сведения о параметрах архивации см. в разделе [резервного КОПИРОВАНИЯ &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
###  <a name="ExampleC"></a> Пример в. шифрование на уровне столбца с помощью асимметричного ключа из хранилища ключей  
 В следующем примере создается симметричный ключ, защищенный асимметричным ключом в хранилище ключей. Затем симметричный ключ используется для шифрования данных в базе данных.  
  
 В этом примере используется асимметричный ключ CONTOSO_KEY из хранилища ключей, который был импортирован или создан ранее, как описано в [шаге 3 раздела 3](#Step3) выше. Чтобы использовать асимметричный ключ в базе данных `ContosoDatabase` , необходимо выполнить инструкцию CREATE ASYMMETRIC KEY еще раз, чтобы предоставить базе данных `ContosoDatabase` ссылку на ключ.  
  
```  
USE [ContosoDatabase];  
GO  
  
-- Create a reference to the key in the key vault  
CREATE ASYMMETRIC KEY CONTOSO_KEY   
FROM PROVIDER [AzureKeyVault_EKM_Prov]  
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',  
CREATION_DISPOSITION = OPEN_EXISTING;  
  
-- Create the data encryption key.  
-- The data encryption key can be created using any SQL Server   
-- supported algorithm or key length.  
-- The DEK will be protected by the asymmetric key in the key vault  
  
CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY  
    WITH ALGORITHM=AES_256  
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;  
  
DECLARE @DATA VARBINARY(MAX);  
  
--Open the symmetric key for use in this session  
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY   
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;  
  
--Encrypt syntax  
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));  
  
-- Decrypt syntax  
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));  
  
--Close the symmetric key  
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)   
 [CREATE CREDENTIAL (Transact-SQL)](/sql/t-sql/statements/create-credential-transact-sql)   
 [CREATE ASYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/create-asymmetric-key-transact-sql)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](/sql/t-sql/statements/create-symmetric-key-transact-sql)   
 [Расширенное управление ключами (EKM)](extensible-key-management-ekm.md)   
 [Включение прозрачного шифрования данных с помощью расширенного управления Ключами](enable-tde-on-sql-server-using-ekm.md)   
 [Шифрование резервной копии](../../backup-restore/backup-encryption.md)   
 [Создание зашифрованной резервной копии](../../backup-restore/create-an-encrypted-backup.md)  
  
  
