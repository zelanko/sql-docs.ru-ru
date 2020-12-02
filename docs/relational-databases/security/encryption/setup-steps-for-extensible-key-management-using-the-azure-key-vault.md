---
title: Настройка расширенного управления ключами прозрачного шифрования данных (TDE) с помощью Azure Key Vault
description: Установка и настройка SQL Server Connector для Azure Key Vault.
ms.custom: seo-lt-2019
ms.date: 10/08/2020
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Extensible Key Management
- EKM, with key vault setup
- SQL Server Connector, setup
- SQL Server Connector
ms.assetid: c1f29c27-5168-48cb-b649-7029e4816906
author: Rupp29
ms.author: arupp
ms.openlocfilehash: 4df1fb243b2e811b216b03ec453164ae1a00b1af
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96130213"
---
# <a name="set-up-sql-server-tde-extensible-key-management-by-using-azure-key-vault"></a>Настройка расширенного управления ключами SQL Server TDE с помощью Azure Key Vault

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

В этой статье мы пройдем по шагам установки и настройки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector для Azure Key Vault.  
  
## <a name="prerequisites"></a>Предварительные требования

Прежде чем приступить к использованию Azure Key Vault с экземпляром SQL Server, убедитесь, что выполнены следующие предварительные требования.  
  
- У вас должна быть подписка Azure.
  
- Установите [Azure PowerShell версии 5.2.0 или более поздней](/powershell/azure/).  

- Создайте экземпляр Azure Active Directory (Azure AD).

- Ознакомьтесь с принципами расширенного управления ключами (EKM) при использовании Azure Key Vault, просмотрев статьи [Расширенное управление ключами с использованием Azure Key Vault (SQL Server)](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  

- Установите версию распространяемого пакета Visual Studio C++, соответствующую используемой версии SQL Server:
  
  Версия SQL Server  | Распространяемый пакет Visual C++
  ---------|---------
  2008, 2008 R2, 2012, 2014 | [Распространяемые пакеты Visual C++ для Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)
  2016 | [Распространяемый пакет Visual C++ для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48145)

## <a name="step-1-set-up-an-azure-ad-service-principal"></a>Шаг 1. Настройка субъекта-службы Azure AD.

Чтобы предоставить экземпляру SQL Server разрешения на доступ к своему хранилищу ключей Azure, потребуется учетная запись субъекта-службы в Azure AD.  
  
1. Войдите на [портал Azure](https://ms.portal.azure.com/) и выполните одно из следующих действий.

    - Нажмите кнопку **Azure Active Directory**.

      ![Снимок экрана: панель "Службы Azure"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-login-portal.png)

    - Выберите **Больше служб**, а затем, в меню **Все службы**, выберите **Azure Active Directory**.

      ![Снимок экрана: панель "Все службы Azure"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-select-aad.png)  

1. Зарегистрируйте приложение в Azure Active Directory, выполнив следующие действия. (Подробные пошаговые инструкции см. в статье "Получение удостоверения приложения" [записи блога об Azure Key Vault](/archive/blogs/kv/azure-key-vault-step-by-step).)

    а. На панели **обзора Azure Active Directory** выберите **Регистрация приложений**.

    ![Снимок экрана: панель "Обзор Azure Active Directory"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-app-register.png)

    b. На панели **Регистрация приложений** выберите **Новая регистрация**.

    ![Снимок экрана: панель "Регистрация приложений"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-new-registration.png)  

    c. На панели **Зарегистрировать приложение** введите имя приложения, доступное для пользователя, а затем выберите **Зарегистрировать**.

    ![Снимок экрана: панель "Зарегистрировать приложение"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-register.png)

    d. На панели слева выберите **Сертификаты и секреты**, затем выберите **Новый секрет клиента**.

    ![Снимок экрана: панель "Сертификаты и секреты"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-certs-secrets.png)  

    д) В разделе **Добавить секрет клиента** введите описание и соответствующий срок действия, а затем выберите **Добавить**.

    ![Снимок экрана: раздел "Добавить секрет клиента"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-add-secret.png)  

    е) В области **Сертификаты & секреты** в разделе **"Значение"** нажмите кнопку **Копировать** рядом со значением секрета клиента, который будет использоваться для создания асимметричного ключа в SQL Server.

    ![Снимок экрана со значением секрета](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-new-secret.png)  

    ж. В левой области выберите **Обзор**, а затем, в поле **Идентификатор приложения (клиента)** , скопируйте значение, которое будет использоваться для создания асимметричного ключа в SQL Server.

    ![Снимок экрана: значения "Идентификатор приложения (клиента)" в области "Обзор"](../../../relational-databases/security/encryption/media/ekm/ekm-part1-aad-appid.png)  

## <a name="step-2-create-a-key-vault"></a>Шаг 2. Создайте хранилище ключей.

Выберите метод, который следует использовать для создания хранилища ключей.

## <a name="azure-portal"></a>[Портал Azure](#tab/portal)

### <a name="create-a-key-vault-by-using-the-azure-portal"></a>Создание хранилища ключей с помощью портала Azure

Портал Azure можно использовать, чтобы создать хранилище ключей, а затем добавить к нему субъект Azure AD.

1. Создайте группу ресурсов.

   Все ресурсы Azure, созданные с помощью портала Azure, должны содержаться в группе ресурсов, которая создается для размещения хранилища ключей. Имя ресурса в этом примере — *ContosoDevRG*. Выберите собственные имена для группы ресурсов и хранилища ключей. Имена всех хранилищ ключей должны быть глобально уникальными.

   На панели **Создать группу ресурсов** в разделе **Сведения о проекте** введите значения, а затем выберите **Просмотр и создание**.

      ![Снимок экрана: панель "Создать группу ресурсов"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-create-resource-group.png)  

1. Создать хранилище ключей.

    На панели **Создать хранилище ключей** выберите вкладку **Основы**, введите соответствующие значения, а затем выберите **Просмотр и создание**.

    ![Снимок экрана: панель "Создать хранилище ключей"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-create-key-vault.png)  

1. На панели **Политики доступа** выберите **Добавить политику доступа**.

    ![Снимок экрана со ссылкой "Добавить политику доступа" в области "Политики доступа"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-add-access-policy.png)  

1. На панели **Добавить политику доступа** выполните следующие действия.
  
    а. В раскрывающемся списке **Настроить из шаблона (необязательно)** выберите **Управление ключами**.

    b. На левой панели выберите вкладку **Разрешения ключа**, а затем убедитесь, что выставлены флажки **Получить**, **Список**, **Распаковка ключа** и **Упаковка ключа**.

    c. Выберите **Добавить**.

    ![Снимок экрана: панель "Добавить политику доступа"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-access-policy-permission.png)

1. На левой панели выберите вкладку **Выбрать субъект**, а затем выполните следующие действия.

    а. На панели **Субъект** в разделе **Выбрать** начните вводить имя приложения Azure AD, а затем в списке результатов выберите приложение, которое нужно добавить.

    ![Снимок экрана: поле поиска приложения на панели "Субъект"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-select-principal.png)  

    b. Нажмите кнопку **Выбрать**, чтобы добавить субъекта в хранилище ключей.

    ![Снимок экрана кнопки выбора на панели "Субъект"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-save-principal.png)

    c. В левом нижнем углу выберите **Добавить**, чтобы сохранить изменения.

    ![Снимок экрана: кнопка "Добавить" на панели "Добавить политику доступа"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-select-principal-new.png)

1. На панели **Key Vault** выберите **Ключи** и введите имя хранилища ключей. Используйте тип ключа **RSA** и задайте размер ключа RSA **2048**. Установите даты активации и истечения срока действия и для параметра **Включен?** выберите значение **Да**.

   ![Снимок экрана: область "Создание ключа"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-add-key-vault-key.png)  

1. На панели **Политики доступа** выберите **Сохранить**.
  
   ![Снимок экрана: кнопка "Сохранить" на панели "Добавить политику доступа"](../../../relational-databases/security/encryption/media/ekm/ekm-part2-save-access-policy.png)  

## <a name="powershell"></a>[PowerShell](#tab/powershell)

### <a name="create-a-key-vault-and-key-by-using-powershell"></a>Создание хранилища ключей и ключа с помощью PowerShell

Ядро СУБД SQL Server будет использовать создаваемые здесь хранилище ключей и ключ для защиты ключа шифрования.  
  
> [!IMPORTANT]
> Подписка, где создается хранилище ключей, должна находиться в том же Azure AD по умолчанию, где был создан субъект-служба Azure AD. Если вы хотите использовать экземпляр Azure AD, отличный от установленного по умолчанию, чтобы создать субъект-службу для соединителя SQL Server, следует изменить экземпляр Azure AD по умолчанию в своей учетной записи Azure перед созданием хранилища ключей. Чтобы узнать, как изменить используемый по умолчанию экземпляр Azure AD на тот, который вы хотите использовать, см. раздел "Часто задаваемые вопросы" статьи [Обслуживание и устранение неполадок соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixB).  
  
1. Установите [Azure PowerShell 5.2.0 или более поздней версии](/powershell/azure/) и войдите в него с помощью следующей команды:  
  
    ```powershell  
    Connect-AzAccount  
    ```  
  
    Инструкция возвращает следующие данные:  
  
    ```console  
    Environment           : AzureCloud  
    Account               : <account_name>  
    TenantId              : <tenant_id>  
    SubscriptionId        : <subscription_id>  
    CurrentStorageAccount :  
    ```  
  
    > [!NOTE]  
    > Если у вас есть несколько подписок и необходимо указать одну из них, которую следует использовать для хранилища, воспользуйтесь `Get-AzSubscription` для просмотра подписок и `Select-AzSubscription` для выбора нужной подписки. В противном случае PowerShell выбирает подписку по умолчанию.  
  
1. Создайте группу ресурсов.

    Все ресурсы Azure, созданные с помощью PowerShell, должны содержаться в группе ресурсов, которая создается для размещения хранилища ключей. Имя ресурса в этом примере — *ContosoDevRG*. Выберите собственные имена для группы ресурсов и хранилища ключей. Имена всех хранилищ ключей должны быть глобально уникальными.  
  
    ```powershell  
    New-AzResourceGroup -Name ContosoDevRG -Location 'East Asia'  
    ```  
  
    Инструкция возвращает следующие данные:  
  
    ```console
    ResourceGroupName: ContosoDevRG  
    Location         : eastasia  
    ProvisioningState: Succeeded  
    Tags             :
    ResourceId       : /subscriptions/<subscription_id>/  
                        resourceGroups/ContosoDevRG  
    ```  
  
    > [!NOTE]
    > Для параметра `-Location` используйте команду `Get-AzureLocation`, чтобы определить, как указать расположение, альтернативное указанному в этом примере. Если требуются дополнительные сведения, введите **Get-Help Get-AzureLocation**.  
  
1. Создать хранилище ключей.

    Для командлета `New-AzKeyVault` необходимо указать имя группы ресурсов, имя хранилища ключей и географическое расположение. Например, для хранилища ключей с именем `ContosoEKMKeyVault` выполните:  
  
    ```powershell  
    New-AzKeyVault -VaultName 'ContosoEKMKeyVault' `  
       -ResourceGroupName 'ContosoDevRG' -Location 'East Asia'  
    ```  
  
    Запишите имя хранилища ключей.  
  
    Инструкция возвращает следующие данные:

    ```console
    Vault Name                       : ContosoEKMKeyVault  
    Resource Group Name              : ContosoDevRG  
    Location                         : East Asia  
    ResourceId                       : /subscriptions/<subscription_id>/  
                                        resourceGroups/ContosoDevRG/providers/  
                                        Microsoft/KeyVault/vaults/ContosoEKMKeyVault  
    Vault URI: https://ContosoEKMKeyVault.vault.azure.net  
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
  
1. Предоставляет субъекту-службе Azure AD разрешений для доступа к Azure Key Vault.  
  
    Вы можете разрешить другим пользователям или приложениям использовать хранилище ключей.  В нашем примере мы используем субъект-службу, созданную в [Шаге 1: настройка субъекта-службы Azure AD](#step-1-set-up-an-azure-ad-service-principal) для авторизации экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    > [!IMPORTANT]
    > Субъект-служба Azure Active Directory должен иметь для хранилища ключей по меньшей мере разрешения *get* (получение), *list* (список),*wrapKey* (упаковка ключа) и *unwrapKey* (распаковка ключа).  
  
    Как показано в следующей команде, вы используете **Идентификатор приложения (клиента)** из [Шага 1: настройка субъекта-службы Azure AD](#step-1-set-up-an-azure-ad-service-principal) для параметра `ServicePrincipalName`. `Set-AzKeyVaultAccessPolicy` выполняется в автоматическом режиме и не выводит никаких данных в случае успешного завершения.  
  
    ```powershell  
    Set-AzKeyVaultAccessPolicy -VaultName 'ContosoEKMKeyVault' `  
      -ServicePrincipalName 9A57CBC5-4C4C-40E2-B517-EA677 `  
      -PermissionsToKeys get, list, wrapKey, unwrapKey  
    ```  
  
    Вызовите командлет `Get-AzKeyVault` , чтобы подтвердить разрешения. В разделе `Access Policies` выходных данных инструкции должно присутствовать имя приложения Azure AD, указанное как другой клиент, имеющий доступ к этому хранилищу ключей.  
  
1. Создайте асимметричный ключ в хранилище ключей. Это можно сделать одним из двух способов: импортом существующего ключа или созданием нового ключа.  

     > [!NOTE]
     > SQL Server поддерживает только 2048-разрядные ключи RSA.

### <a name="best-practices"></a>Рекомендации

Для обеспечения быстрого восстановления ключей и возможности доступа к данным за пределами Azure мы рекомендуем следующее.

- Создайте ключ шифрования локально, на локальном аппаратном модуле безопасности (HSM). Это должен быть асимметричный ключ RSA 2048, так как SQL Server поддерживает только такие ключи.
- Импортируйте ключ шифрования в Azure Key Vault. Этот процесс описан в последующих разделах.
- Перед первым использованием ключа в хранилище ключей Azure создайте резервную копию ключа из Azure Key Vault. Дополнительные сведения см. в описании команды [Backup-AzureKeyVaultKey]().
- При каждом внесении изменений в ключ (например, при добавлении списков управления доступом, тегов, ключевых атрибутов) создавайте новую резервную копию ключа из Azure Key Vault.

  > [!NOTE]
  > Резервное копирование ключа из Azure Key Vault позволяет получить файл, который можно сохранить в любом расположении.

### <a name="types-of-keys"></a>Типы ключей

Существует два типа ключей, которые можно создать в Azure Key Vault и которые работают с SQL Server. Оба типа — асимметричные 2048-битные RSA-ключи.  
  
- **Защищенные с помощью ПО**. Обрабатываются в программном обеспечении и шифруются в неактивном состоянии. Операции с ключами, защищенными программным обеспечением, выполняются на виртуальных машинах Azure. Рекомендуется использовать этот тип для ключей, которые не используются в рабочем развертывании.  

- **Защищенные модулем HSM**. Создаются и защищаются с помощью аппаратного модуля безопасности (HSM), что обеспечивает дополнительную защиту. Стоимость составляет около 1 доллара США за версию ключа.  
  
    > [!IMPORTANT]
    > Для соединителя SQL Server используйте только символы a–z, A–Z, 0–9 и "-" при длине не более 26 знаков.
    > Разные версии ключа, имеющие одинаковое имя в хранилище ключей Azure, не будут работать с соединителем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы сменить ключ в Azure Key Vault, используемый [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], обратитесь к описанию этапов смены ключей в разделе "А. Инструкции по обслуживанию соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]" статьи [Обслуживание и устранение неполадок соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md).  

### <a name="import-an-existing-key"></a>Импорт существующего ключа
  
Если у вас есть 2048-битный RSA-ключ, защищенный программным обеспечением, можно отправить его в свое хранилище ключей Azure. Например, при наличии PFX-файла, сохраненного на диске `C:\\`, в файле с именем *softkey.pfx*, который необходимо отправить в хранилище ключей Azure, чтобы задать переменную `securepfxpwd` в качестве пароля `12987553` для PFX-файла, введите следующую команду:  
  
``` powershell  
$securepfxpwd = ConvertTo-SecureString -String '12987553' `  
  -AsPlainText -Force  
```  

Затем, чтобы импортировать ключ из PFX-файла, который защищает его с помощью аппаратных средств (рекомендуется) в службе Azure Key Vault, введите следующую команду:  
  
``` powershell  
    Add-AzureKeyVaultKey -VaultName 'ContosoKeyVault' `  
      -Name 'ContosoFirstKey' -KeyFilePath 'c:\softkey.pfx' `  
      -KeyFilePassword $securepfxpwd $securepfxpwd  -Destination 'HSM'  
```  

> [!CAUTION]
> Импорт асимметричного ключа настоятельно рекомендуется для рабочих сценариев, так как это позволяет администратору передать ключ в систему депонирования ключей. Если в хранилище создается асимметричный ключ, он не может быть передан, так как закрытый ключ не может покидать хранилище. Ключи, используемые для защиты важных данных, должны быть переданы. Потеря асимметричного ключа приведет к невозможности восстановить данные.  

### <a name="create-a-new-key"></a>Создание ключа

Кроме того, можно создать новый ключ шифрования непосредственно в Azure Key Vault и защитить его с помощью программного обеспечения или модуля HSM.  В этом примере мы создадим ключ, защищенный программным обеспечением, используя командлет `Add-AzureKeyVaultKey`:  

``` powershell  
Add-AzureKeyVaultKey -VaultName 'ContosoEKMKeyVault' `  
  -Name 'ContosoRSAKey0' -Destination 'Software'  
```  
  
Инструкция возвращает следующие данные:  
  
```console
Attributes : Microsoft.Azure.Commands.KeyVault.Models.KeyAttributes  
Key        :  {"kid":"https:contosoekmkeyvault.azure.net/keys/  
                ContosoRSAKey0/<guid>","dty":"RSA:,"key_ops": ...  
VaultName  : contosodevkeyvault  
Name       : contosoRSAKey0  
Version    : <guid>  
Id         : https://contosoekmkeyvault.vault.azure.net:443/  
              keys/ContosoRSAKey0/<guid>  
```  

> [!IMPORTANT]
> Хранилище ключей поддерживает несколько версий ключа с одним именем, однако для ключей, используемых соединителем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], не следует применять управление версиями или смену ключей. Если администратору требуется сменить ключ, используемый для шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], следует создать ключ с другим именем в хранилище и использовать его для шифрования ключа шифрования.  

---

## <a name="step-3-install-the-ssnoversion-connector"></a>Шаг 3. Установка соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]

Скачайте Соединитель SQL Server из [Центра загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=521700). Загрузку должен выполнить администратор компьютера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

> [!NOTE]
> - Соединитель SQL Server версии 1.0.0.440 и более ранних версий были заменены и больше не поддерживаются в рабочих средах. Вместо них используются инструкции на странице [Обслуживание и устранение неполадок соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md) в разделе [Обновление соединителя SQL Server](sql-server-connector-maintenance-troubleshooting.md#upgrade-of--connector).
> - Начиная с версии 1.0.3.0, соединитель SQL Server передает соответствующие сообщения об ошибках в журналы событий Windows для устранения неполадок.
> - Начиная с версии 1.0.4.0, доступна поддержка частных облаков Azure, включая Azure для Китая, Azure для Германии и Azure для государственных организаций.
> - В версии 1.0.5.0 внесено критическое изменение, касающееся алгоритма отпечатков. После обновления до версии 1.0.5.0 восстановление базы данных может завершаться сбоем. Дополнительные сведения см. в [статье базы знаний 447099](https://support.microsoft.com/help/4470999/db-backup-problems-to-sql-server-connector-for-azure-1-0-5-0).
> - **Начиная с версии 1.0.5.0 (метка времени: сентябрь 2020 г.) соединитель SQL Server поддерживает фильтрацию сообщений и логику повторных попыток сетевого запроса.**
  
  ![Снимок экрана мастера установки соединителя SQL Server.](../../../relational-databases/security/encryption/media/ekm/ekm-connector-install.png)  
  
По умолчанию соединитель устанавливается в C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault. Эту папку можно изменить во время установки. Если вы измените ее, измените сценарии в следующем разделе.  
  
У соединителя нет интерфейса, но, если он будет установлен успешно, на компьютере устанавливается *Microsoft.AzureKeyVaultService.EKM.dll*. Эта сборка — DLL-библиотека поставщика расширенного управления ключами, которую необходимо зарегистрировать в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции `CREATE CRYPTOGRAPHIC PROVIDER`.  
  
Установка Соединителя SQL Server также позволяет при необходимости скачать примеры скриптов для шифрования SQL Server.  
  
Просмотреть описания кодов ошибок, параметры конфигурации и задачи обслуживания для соединителя SQL Server можно в следующих разделах.  
  
- [А. Инструкции по обслуживанию для соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixA)  
- [В. Описания кодов ошибок для соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixC)  
  
## <a name="step-4-configure-ssnoversion"></a>Шаг 4. Настройка [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  

Сведения о минимальном уровне разрешений для выполнения каждого из описанных здесь действий см. в разделе [Б. Часто задаваемые вопросы](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md#AppendixB).  
  
1. Запустите *sqlcmd.exe* или откройте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Studio.  
  
1. Настройте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для использования расширенного управления ключами, выполнив следующий сценарий [!INCLUDE[tsql](../../../includes/tsql-md.md)]:  
  
    ```sql  
    -- Enable advanced options.  
    USE master;  
    GO  

    EXEC sp_configure 'show advanced options', 1;  
    GO  
    RECONFIGURE;  
    GO  

    -- Enable EKM provider  
    EXEC sp_configure 'EKM provider enabled', 1;  
    GO  
    RECONFIGURE;  
    ```  
  
1. Зарегистрируйте соединитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве поставщика расширенного управления ключами с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    Создайте поставщик служб шифрования с помощью соединителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который является поставщиком расширенного управления ключами для Azure Key Vault.
    В этом примере имя поставщика — `AzureKeyVault_EKM`.  
  
    ```sql  
    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO  
    ```  

    > [!NOTE]
    > Длина пути файла не может превышать 256 символов.  
  
1. Настройте учетные данные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], чтобы использовать хранилище ключей.  
  
    Учетные данные необходимо добавить к каждому имени входа, которое будет выполнять шифрование с использованием ключа из хранилища ключей. К ним могут относиться:  
  
    - Имя входа администратора [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которое будет использовать хранилище ключей для настройки сценариев шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и управления ими.  
  
    - Другие имена входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые могут включать TDE или другие функции шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    Между учетными данными и именами входа имеется прямое соответствие. То есть каждое имя входа должно иметь уникальные учетные данные.  
  
    Измените приведенный ниже сценарий [!INCLUDE[tsql](../../../includes/tsql-md.md)] следующим образом.  
  
    - Измените аргумент `IDENTITY` (`ContosoEKMKeyVault`), чтобы он указывал на хранилище ключей Azure.
      - Если используется *глобальная служба Azure*, замените аргумент `IDENTITY` на имя своего хранилища Azure Key Vault из [Шага 2: создание хранилища ключей](#step-2-create-a-key-vault).
      - Если вы используете *частное облако* Azure (например, Azure для государственных организаций, Azure для Китая (21Vianet) или Azure для Германии), замените аргумент `IDENTITY` на URI хранилища, который возвращается на шаге 3 раздела [Создание хранилища ключей и ключа с помощью PowerShell](#create-a-key-vault-and-key-by-using-powershell). Не включайте https:// в URI хранилища.
    - Замените первую часть аргумента `SECRET` на идентификатор клиента Azure Active Directory из [Шага 1: настройка субъекта-службы Azure AD](#step-1-set-up-an-azure-ad-service-principal). В этом примере **идентификатором клиента** является `9A57CBC54C4C40E2B517EA677E0EFA00`.  
  
      > [!IMPORTANT]
      > Необходимо удалить дефисы из идентификатора приложения (клиента).  
  
    - Выполните вторую часть аргумента `SECRET` с **Секретом клиента** из [Шага 1: настройка субъекта-службы Azure AD](#step-1-set-up-an-azure-ad-service-principal).  В этом примере секретом клиента является `08:k?[:XEZFxcwIPvVVZhTjHWXm7w1?m`. Окончательная строка аргумента `SECRET` будет представлять собой длинную последовательность букв и цифр без дефисов.  
  
    ```sql  
    USE master;  
    CREATE CREDENTIAL sysadmin_ekm_cred
        WITH IDENTITY = 'ContosoEKMKeyVault',                            -- for public Azure
        -- WITH IDENTITY = 'ContosoEKMKeyVault.vault.usgovcloudapi.net', -- for Azure Government
        -- WITH IDENTITY = 'ContosoEKMKeyVault.vault.azure.cn',          -- for Azure China 21Vianet
        -- WITH IDENTITY = 'ContosoEKMKeyVault.vault.microsoftazure.de', -- for Azure Germany
               --<----Application (Client) ID ---><--Azure AD app (Client) ID secret-->
        SECRET = '9A57CBC54C4C40E2B517EA677E0EFA0008:k?[:XEZFxcwIPvVVZhTjHWXm7w1?m'
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM;  
  
    -- Add the credential to the SQL Server administrator's domain login
    ALTER LOGIN [<domain>\<login>]  
    ADD CREDENTIAL sysadmin_ekm_cred;  
    ```  
  
    Пример использования переменных для аргумента `CREATE CREDENTIAL` и программного удаления дефисов из идентификатора клиента см. в [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md).  
  
1. Откройте ключ Azure Key Vault в своем экземпляре SQL Server.  

    Независимо от того, создали ли вы новый ключ или импортировали асимметричный ключ, как описано в [Шаге 2: создание хранилища ключей](#step-2-create-a-key-vault), необходимо открыть его. Для этого укажите имя ключа в приведенном ниже сценарии [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
    - Замените `EKMSampleASYKey` на имя, которое вы хотите использовать для ключа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
    - Замените `ContosoRSAKey0` на имя ключа в Azure Key Vault.  
  
    ```sql  
    CREATE ASYMMETRIC KEY EKMSampleASYKey
    FROM PROVIDER [AzureKeyVault_EKM]  
    WITH PROVIDER_KEY_NAME = 'ContosoRSAKey0',  
    CREATION_DISPOSITION = OPEN_EXISTING;  
    ```  

1. Создайте новое имя входа с помощью асимметричного ключа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], созданного на предыдущем шаге.

     ```sql  
    --Create a Login that will associate the asymmetric key to this login
    CREATE LOGIN TDE_Login
    FROM ASYMMETRIC KEY EKMSampleASYKey;
    ```  

1. Создайте новое имя входа из асимметричного ключа в SQL Server. Удалите сопоставление учетных данных из шага 4: настройка SQL Server таким образом, чтобы учетные данные могли быть сопоставлены с новым именем входа.

     ```sql  
    --Now drop the credential mapping from the original association
    ALTER LOGIN [<domain>\<login>]
    DROP CREDENTIAL sysadmin_ekm_cred;
    ```

1. Измените новое имя входа и сопоставьте учетные данные расширенного управления ключами с новым именем входа.

     ```sql  
    --Now add the credential mapping to the new Login
    ALTER LOGIN TDE_Login
    ADD CREDENTIAL sysadmin_ekm_cred;
    ```  

1. Создайте тестовую базу данных, которая будет зашифрована с помощью этого ключа хранилища ключей Azure.

     ```sql
    --Create a test database that will be encrypted with the Azure key vault key
    CREATE DATABASE TestTDE
    ```  

1. Создайте ключ шифрования базы данных с помощью ASYMMETRIC KEY (EKMSampleASYKey).

    ```sql  
    --Create an ENCRYPTION KEY using the ASYMMETRIC KEY (EKMSampleASYKey)
    CREATE DATABASE ENCRYPTION KEY
    WITH ALGORITHM = AES_256
    ENCRYPTION BY SERVER ASYMMETRIC KEY EKMSampleASYKey;
    ```
  
1. Зашифруйте тестовую базу данных. Включите TDE, установив ENCRYPTION ON.

     ```sql  
    --Enable TDE by setting ENCRYPTION ON
    ALTER DATABASE TestTDE
    SET ENCRYPTION ON;  
     ```  

1. Очистите тестовые объекты. Удалите все объекты, созданные в этом тестовом сценарии.

    ```sql  
    -- CLEAN UP
    USE Master
    ALTER DATABASE [TestTDE] SET SINGLE_USER WITH ROLLBACK IMMEDIATE
    DROP DATABASE [TestTDE]

    ALTER LOGIN [TDE_Login] DROP CREDENTIAL [sysadmin_ekm_cred]
    DROP LOGIN [TDE_Login]

    DROP CREDENTIAL [sysadmin_ekm_cred]  

    USE MASTER
    DROP ASYMMETRIC KEY [EKMSampleASYKey]
    DROP CRYPTOGRAPHIC PROVIDER [AzureKeyVault_EKM]
    ```  

Примеры сценариев см. в блоге [Прозрачное шифрование данных и расширенное управление ключами SQL Server с помощью Azure Key Vault](https://techcommunity.microsoft.com/t5/sql-server/intro-sql-server-transparent-data-encryption-and-extensible-key/ba-p/1427549).

## <a name="next-steps"></a>Дальнейшие действия  
  
После настройки базовой конфигурации см. статью [Использование соединителя SQL Server с компонентами шифрования SQL](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md).
  
## <a name="see-also"></a>См. также раздел  

- [Расширенное управление ключами с помощью Azure Key Vault](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)
- [Обслуживание и устранение неполадок соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)
