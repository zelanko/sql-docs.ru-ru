---
title: Расширенное управление ключами SQL Server TDE с помощью Azure Key Vault (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 08/24/2018
ms.prod: sql
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault setup
- SQL Server Connector, setup
- SQL Server Connector
ms.assetid: c1f29c27-5168-48cb-b649-7029e4816906
caps.latest.revision: 34
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: b37105bb247391748f466f406c6b6dd8403e720b
ms.sourcegitcommit: 3762dd447ca4bb449eda8476e72f393db0851b38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46013819"
---
# <a name="sql-server-tde-extensible-key-management-using-azure-key-vault---setup-steps"></a>Расширенное управление ключами SQL Server TDE с помощью Azure Key Vault (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Ниже приведены пошаговые инструкции по установке и настройке Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для Azure Key Vault.  
  
## <a name="before-you-start"></a>Перед началом работы  
 Чтобы использовать хранилище ключей Azure с SQL Server, необходимо выполнить несколько предварительных условий.  
  
-   Наличие подписки Azure  
  
-   Установка последней версии [Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) (5.2.0 или более поздней).  

-   Создание Azure Active Directory  

-   Ознакомление с субъектами хранилища расширенного управления ключами, использующими хранилище ключей Azure, с помощью статьи [Расширенное управление ключами с помощью хранилища ключей Azure &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  

-   Установите подходящую версию распространяемого пакета Visual Studio C++ с учетом используемой версии SQL Server:
  
Версия SQL Server  |Ссылка для установки распространяемого пакета    
---------|--------- 
2008, 2008 R2, 2012, 2014 | [Распространяемые пакеты Visual C++ для Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)    
2016 | [Распространяемый пакет Visual C++ для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48145)    
 
  
## <a name="part-i-set-up-an-azure-active-directory-service-principal"></a>Часть I. Настройка субъекта-службы Azure Active Directory  
 Чтобы предоставить SQL Server разрешения на доступ к вашему хранилищу ключей Azure, потребуется учетная запись субъекта-службы в Azure Active Directory (AAD).  
  
1.  Перейдите на [портал Azure](https://ms.portal.azure.com/) и выполните вход.  
  
2.  Зарегистрируйте приложение в Azure Active Directory. Подробные пошаговые инструкции по регистрации приложения см. в статье **Получение удостоверения приложения** записи блога [о хранилище ключей Azure](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/).  
  
3.  Скопируйте **идентификатор клиента** и **секрет клиента** , чтобы в дальнейшем использовать их для предоставления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] доступа к хранилищу ключей.  
  
 ![ekm-client-id](../../../relational-databases/security/encryption/media/ekm-client-id.png "ekm-client-id")  
  
 ![ekm-key-id](../../../relational-databases/security/encryption/media/ekm-key-id.png "ekm-key-id")  
  
## <a name="part-ii-create-a-key-vault-and-key"></a>Часть II. Создание хранилища ключей и ключа  
 Компонент SQL Server Database Engine будет использовать создаваемое здесь хранилище ключей и ключ для защиты ключа шифрования.  
  
> [!IMPORTANT]  
>  Подписка, где создается хранилище ключей, должна находиться в том же Azure Active Directory по умолчанию, где была создана субъект-служба Azure Active Directory. Если вы хотите использовать Active Directory, отличный от установленного по умолчанию, чтобы создать субъект-службу для соединителя SQL Server, следует изменить Active Directory по умолчанию в вашей учетной записи Azure перед созданием хранилища ключей. Узнать о том, как изменить Active Directory по умолчанию на нужный вам, можно в [часто задаваемых вопросах](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixB)по соединителю SQL Server.  
  
1.  **Открытие PowerShell и вход**  
  
     Установите и запустите [последнюю версию Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/) (5.2.0 или более позднюю). Войдите в учетную запись Azure с помощью следующей команды:  
  
    ```powershell  
    Login-AzureRmAccount  
    ```  
  
     Инструкция возвращает следующие данные:  
  
    ```  
    Environment           : AzureCloud  
    Account               : <account_name>  
    TenantId              : <tenant_id>  
    SubscriptionId        : <subscription_id>  
    CurrentStorageAccount :  
    ```  
  
    > [!NOTE]  
    >  Если у вас есть несколько подписок и необходимо указать одну из них, чтобы использовать для хранилища, воспользуйтесь `Get-AzureRmSubscription` для просмотра подписок и `Select-AzureRmSubscription` для выбора нужной подписки. В противном случае PowerShell выбирает подписку по умолчанию.  
  
2.  **Создание группы ресурсов**  
  
     Все ресурсы Azure, созданные посредством Azure Resource Manager, должны находиться в группах ресурсов. Создайте группу ресурсов для размещения хранилища ключей. В этом примере используется `ContosoDevRG`. Выберите свои **уникальные** имена для группы ресурсов и хранилища ключей, так как имена всех хранилищ ключей являются глобально уникальными.  
  
    ```powershell  
    New-AzureRmResourceGroup -Name ContosoDevRG -Location 'East Asia'  
    ```  
  
     Инструкция возвращает следующие данные:  
  
    ```  
    ResourceGroupName: ContosoDevRG  
    Location         : eastasia  
    ProvisioningState: Succeeded  
    Tags             :   
    ResourceId       : /subscriptions/<subscription_id>/  
                        resourceGroups/ContosoDevRG  
    ```  
  
    > [!NOTE]  
    >  Для `-Location parameter`используйте команду `Get-AzureLocation` , чтобы определить, как можно указать альтернативное расположение в этом примере. Если требуются дополнительные сведения, введите: `Get-Help Get-AzureLocation`  
  
3.  **Создание хранилища ключей**  
  
     Для командлета `New-AzureRmKeyVault` необходимо указать имя группы ресурсов, имя хранилища ключей и географическое расположение. Например, для хранилища ключей с именем `ContosoDevKeyVault`введите:  
  
    ```powershell  
    New-AzureRmKeyVault -VaultName 'ContosoDevKeyVault' `  
       -ResourceGroupName 'ContosoDevRG' -Location 'East Asia'  
    ```  
  
     Запишите имя хранилища ключей.  
  
     Инструкция возвращает следующие данные:  
  
    ```  
    Vault Name                       : ContosoDevKeyVault  
    Resource Group Name              : ContosoDevRG  
    Location                         : East Asia  
    ResourceId                       : /subscriptions/<subscription_id>/  
                                        resourceGroups/ContosoDevRG/providers/  
                                        Microsoft/KeyVault/vaults/ContosoDevKeyVault  
    Vault URI: https://ContosoDevKeyVault.vault.azure.net  
    Tenant ID                        : <tenant_id>  
    SKU                              : Standard  
    Enabled For Deployment?          : False  
    Enabled For Template Deployment? : False  
    Enabled For Disk Encryption?     : False  
    Access Policies                  :  
             Tenant ID              : <tenant_id>  
             Object ID              : <object_id>  
             Application ID         :   
             Display Name           : <display_name>  
             Permissions to Keys    : get, create, delete, list, update, import,   
                                      backup, restore  
             Permissions to Secrets : all  
    Tags                             :  
    ```  
  
4.  **Предоставление субъекту-службе Azure Active Directory разрешений для доступа к хранилищу ключей**  
  
     Вы можете разрешить другим пользователям или приложениям использовать хранилище ключей.   
    В этом случае воспользуемся субъектом-службой Azure Active Directory, созданным в части I для авторизации экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    > [!IMPORTANT]  
    >  Субъект-служба Azure Active Directory должен иметь для хранилища ключей по меньшей мере разрешения `get`, `wrapKey` и `unwrapKey`.  
  
     Как показано ниже, используйте **идентификатор клиента** из части I для параметра `ServicePrincipalName` . `Set-AzureRmKeyVaultAccessPolicy` выполняется в автоматическом режиме и не выводит никаких данных в случае успешного завершения.  
  
    ```powershell  
    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoDevKeyVault'`  
      -ServicePrincipalName EF5C8E09-4D2A-4A76-9998-D93440D8115D `  
      -PermissionsToKeys get, wrapKey, unwrapKey  
    ```  
  
     Вызовите командлет `Get-AzureRmKeyVault` , чтобы подтвердить разрешения. В разделе Access Policies (Политики доступа) выходных данных инструкции должно присутствовать имя приложения AAD, указанное как другой клиент, имеющий доступ к этому хранилищу ключей.  
  
       
5.  **Создание асимметричного ключа в хранилище ключей**  
  
     Создать ключ в хранилище ключей Azure можно двумя способами: импортировать существующий ключ или создать новый.  
                  
      > [!NOTE]
        >  SQL Server поддерживает только 2048-битные RSA-ключи.
        
    ### <a name="best-practice"></a>Рекомендации
    
    Для обеспечения быстрого восстановления ключей и возможности доступа к данным за пределами Azure мы рекомендуем следующее.
 
    1. Создайте ключ шифрования локально на локальном устройстве HSM. (Это должен быть асимметричный ключ RSA 2048, так как SQL Server поддерживает только такие ключи.)
    2. Импортируйте ключ шифрования в хранилище ключей Azure. Ниже эта процедура описана более подробно.
    3. Перед первым использованием ключа в хранилище ключей Azure создайте резервную копию ключа из хранилища ключей Azure. См. дополнительные сведения о команде [Backup-AzureKeyVaultKey](https://msdn.microsoft.com/library/mt126292.aspx) .
    4. При каждом внесении изменений в ключ (например, при добавлении списков управления доступом, тегов, ключевых атрибутов) снова создайте резервную копию ключа из Azure Key Vault.

        > [!NOTE]  
        >  Резервное копирование ключа из Azure Key Vault позволяет получить файл, который можно сохранить в любом расположении.

    ### <a name="types-of-keys"></a>Типы ключей:
    Существует два типа ключей, которые можно создать в Azure Key Vault и которые работают с SQL Server. Оба являются асимметричными 2048-битными RSA-ключами.  
  
    -   **Защищенные программным обеспечением:** обрабатываются в программном обеспечении и шифруются в неактивном состоянии. Операции с ключами, защищенными программным обеспечением, выполняются на виртуальных машинах Azure. Рекомендуется для ключей, не используемых в рабочей среде.  
  
    -   **Защищенные с помощью HSM:** создаются и защищаются аппаратным модулем безопасности HSM для обеспечения дополнительной безопасности. Стоят около 1 доллара США за версию ключа.  
  
        > [!IMPORTANT]  
        >  Соединителю SQL Server требуется, чтобы имя ключа содержало только символы a–z, A–Z, 0–9 и "-" и имело длину не более 26 знаков.   
        > Разные версии ключа, имеющие одинаковое имя в хранилище ключей Azure, не будут работать с Соединителем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы сменить ключ хранилища ключей Azure, используемый [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], обратитесь к инструкциям по смене ключей в статье [Соединитель SQL Server, приложение](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md).  

    ### <a name="import-an-existing-key"></a>Импорт существующего ключа   
  
    Если у вас есть 2048-битный RSA-ключ, защищенный программным обеспечением, можно отправить его в хранилище ключей Azure. Например, при наличии PFX-файла, сохраненного на диске `C:\\` в файле с именем `softkey.pfx` , который необходимо отправить в хранилище ключей Azure, чтобы задать для переменной `securepfxpwd` пароль `12987553` для PFX-файла, введите следующую команду:  
  
    ``` powershell  
    $securepfxpwd = ConvertTo-SecureString –String '12987553' `  
      –AsPlainText –Force  
    ```  
  
    Затем, чтобы импортировать ключ из PFX-файла, который защищает его с помощью аппаратных средств (рекомендуется) в службе хранилища ключей, введите следующую команду:  
  
    ``` powershell  
        Add-AzureKeyVaultKey -VaultName 'ContosoKeyVault' `  
          -Name 'ContosoFirstKey' -KeyFilePath 'c:\softkey.pfx' `  
          -KeyFilePassword $securepfxpwd $securepfxpwd  -Destination 'HSM'  
    ```  
 
    > [!IMPORTANT]  
    > Импорт асимметричного ключа настоятельно рекомендуется для рабочих сценариев, так как это позволяет администратору передать ключ в систему переноса ключей. Если в хранилище создается асимметричный ключ, он не может быть передан, так как закрытый ключ не может покидать хранилище. Ключи, используемые для защиты важных данных, должны быть перенесены. Потеря асимметричного ключа приведет к невозможности восстановить данные.  

    ### <a name="create-a-new-key"></a>Создание ключа
    #### <a name="example"></a>Пример  
    Кроме того, можно создать ключ шифрования непосредственно в Azure Key Vault и защитить его с помощью программного обеспечения или HSM.  В этом примере мы создадим ключ, защищенный программным обеспечением, используя `Add-AzureKeyVaultKey cmdlet`:  

    ``` powershell  
    Add-AzureKeyVaultKey -VaultName 'ContosoDevKeyVault' `  
      -Name 'ContosoRSAKey0' -Destination 'Software'  
    ```  
  
    Инструкция возвращает следующие данные:  
  
    ```  
    Attributes : Microsoft.Azure.Commands.KeyVault.Models.KeyAttributes  
    Key        :  {"kid":"https:contosodevKeyVault.azure.net/keys/  
                   ContosoRSAKey0/<guid>","dty":"RSA:,"key_ops": ...  
    VaultName  : contosodevkeyvault  
    Name       : contosoRSAKey0  
    Version    : <guid>  
    Id         : https://contosodevkeyvault.vault.azure.net:443/  
                 keys/ContosoRSAKey0/<guid>  
    ```  
 > [!IMPORTANT]  
    >  Хранилище ключей поддерживает несколько версий ключа с одним именем, однако для ключей, используемых Соединителем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , не следует применять управление версиями или смену ключей. Если администратору требуется откатить ключ, используемый для шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , следует создать ключ с другим именем в хранилище и использовать его для шифрования ключа шифрования базы данных.  
   
  
## <a name="part-iii-install-the-includessnoversionincludesssnoversion-mdmd-connector"></a>Часть III. Установка Соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 Скачайте Соединитель SQL Server из [Центра загрузки Майкрософт](http://go.microsoft.com/fwlink/p/?LinkId=521700). (Это должен сделать администратор компьютера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .)  

> [!NOTE]  
>  Версии 1.0.0.440 и старше были заменены и больше не поддерживаются в рабочих средах. Выполните обновление до версии 1.0.1.0 или более поздней, посетив [Центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=45344) и используя инструкции на странице [Соединитель SQL Server, приложение](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md) в разделе "Обновление соединителя SQL Server".
  
 ![ekm-connector-install](../../../relational-databases/security/encryption/media/ekm-connector-install.png "ekm-connector-install")  
  
 По умолчанию соединитель устанавливается в папку C:\Program Files\SQL Server Connector для Microsoft Azure Key Vault. Эту папку можно изменить во время установки. (В этом случае измените и следующие скрипты.)  
  
 У соединителя нет интерфейса, но, если он будет установлен успешно, на компьютере устанавливается **Microsoft.AzureKeyVaultService.EKM.dll** . Это DLL-библиотека поставщика расширенного управления ключами, которую необходимо зарегистрировать в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции `CREATE CRYPTOGRAPHIC PROVIDER` .  
  
 Установка Соединителя SQL Server также позволяет при необходимости скачать примеры скриптов для шифрования SQL Server.  
  
 Чтобы просмотреть описания кодов ошибок, параметры конфигурации и задачи обслуживания для соединителя SQL Server, откройте приложения в конце этого раздела.  
  
-   [A. Инструкции по обслуживанию для соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixA)  
  
-   [C. Описания кодов ошибок для соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixC)  
  
  
## <a name="part-iv-configure-includessnoversionincludesssnoversion-mdmd"></a>Часть IV. Настройка [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 Сведения о минимальном уровне разрешений для выполнения каждого из описанных здесь действий см. в разделе [Б. Часто задаваемые вопросы](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixB).  
  
1.  **Запуск sqlcmd.exe или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Studio**  
  
2.  **Настройка [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для использования расширенного управления ключами**  
  
     Выполните следующий скрипт [!INCLUDE[tsql](../../../includes/tsql-md.md)] , чтобы настроить [!INCLUDE[ssDE](../../../includes/ssde-md.md)] для использования поставщика расширенного управления ключами.  
  
    ```sql  
    -- Enable advanced options.  
    USE master;  
    GO  
  
    sp_configure 'show advanced options', 1;  
    GO  
    RECONFIGURE;  
    GO  
  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1;  
    GO  
    RECONFIGURE;  
    ```  
  
3.  **Регистрация (создание) соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве поставщика расширенного управления ключами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**  
  
     — Создайте поставщик служб шифрования с помощью соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который является поставщиком расширенного управления ключами для Azure Key Vault.    
    В этом примере используется имя `AzureKeyVault_EKM_Prov`.  
  
    ```sql  
    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Длина пути файла не может превышать 256 символов.  
  
  
4.  **Настройка учетных данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для хранилища ключей**  
  
     Учетные данные необходимо добавить к каждому имени входа, которое будет выполнять шифрование с использованием ключа из хранилища ключей. К ним могут относиться:  
  
    -   имя входа администратора [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которое будет использовать хранилище ключей для настройки сценариев шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и управления ими;  
  
    -   другие имена входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которые могут включить прозрачное шифрование данных (TDE), или другие функции шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
     Между учетными данными и именами входа имеется прямое соответствие. То есть каждое имя входа должно иметь уникальные учетные данные.  
  
     Измените приведенный ниже скрипт [!INCLUDE[tsql](../../../includes/tsql-md.md)] следующим образом.  
  
    -   Измените аргумент `IDENTITY` (`ContosoDevKeyVault`), чтобы он указывал на хранилище ключей Azure.
        - Если вы используете **глобальную службу Azure**, замените аргумент `IDENTITY` на имя вашего хранилища Azure Key Vault из части II.
        - Если вы используете **частное облако Azure** (например, Azure для государственных организаций, китайскую или немецкую версию Azure), замените аргумент `IDENTITY` на URI хранилища, возвращенный на шаге 3 в части II. Не включайте https:// в URI хранилища.   
    -   Замените первую часть аргумента `SECRET` на **идентификатор клиента** Azure Active Directory из части I. В этом примере **идентификатор клиента** имеет значение `EF5C8E094D2A4A769998D93440D8115D`.  
  
        > [!IMPORTANT]  
        >  Необходимо удалить дефисы из **идентификатора клиента**.  
  
    -   Дополните вторую часть аргумента `SECRET` **секретом клиента** из части I. В этом примере **секрет клиента** из части I имеет значение `Replace-With-AAD-Client-Secret`. Окончательная строка аргумента `SECRET` будет представлять собой длинную последовательность букв и цифр *без дефисов*.  
  
    ```sql  
    USE master;  
    CREATE CREDENTIAL sysadmin_ekm_cred   
        WITH IDENTITY = 'ContosoDevKeyVault', -- for public Azure
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.usgovcloudapi.net', -- for Azure Government
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.azure.cn', -- for Azure China
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.microsoftazure.de', -- for Azure Germany   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DReplace-With-AAD-Client-Secret'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;  
  
    -- Add the credential to the SQL Server administrator's domain login   
    ALTER LOGIN [<domain>\<login>]  
    ADD CREDENTIAL sysadmin_ekm_cred;  
    ```  
  
     Пример использования переменных для аргументов **CREATE CREDENTIAL** и программного удаления дефисов из идентификатора клиента см. в статье [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md).  
  
5.  **Открытие хранилища ключей Azure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**  
  
     Если вы импортировали асимметричный ключ, как описано в части II, откройте этот ключ, указав его имя в следующем скрипте [!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
    -   Замените `CONTOSO_KEY` на имя, которое вы хотите использовать для ключа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    -   Замените `ContosoRSAKey0` на имя ключа в хранилище ключей Azure.  
  
    ```sql  
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH PROVIDER_KEY_NAME = 'ContosoRSAKey0',  
    CREATION_DISPOSITION = OPEN_EXISTING;  
    ```  
## <a name="next-step"></a>Следующий шаг  
  
После выполнения базовой конфигурации см. статью [Использование Соединителя SQL Server с компонентами шифрования SQL](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md)   
  
## <a name="see-also"></a>См. также:  
 [Расширенное управление ключами с помощью хранилища ключей Azure](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)   
[Соединитель SQL Server, приложение](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)
