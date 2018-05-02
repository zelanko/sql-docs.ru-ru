---
title: Включение прозрачного шифрования данных SQL с использованием собственного ключа Azure Key Vault с помощью PowerShell и CLI | Документы Майкрософт
description: Сведения о настройке базы данных и хранилища данных SQL Azure для использования прозрачного шифрования данных (TDE) с целью шифрования хранящихся данных с помощью PowerShell или CLI.
keywords: ''
documentationcenter: ''
author: aliceku
manager: craigg
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.component: security
ms.workload: On Demand
ms.tgt_pltfrm: ''
ms.devlang: azurecli, powershell
ms.topic: article
ms.date: 03/15/2018
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: eed635cc4b58c5ec975f0b77f8e3b69f87fd65ff
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vault"></a>Включение прозрачного шифрования данных с использованием собственного ключа из Azure Key Vault с помощью PowerShell и CLI

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

В этом практическом руководстве рассматриваются способы использования ключа из Azure Key Vault для прозрачного шифрования данных (TDE) в базе данных или хранилище данных SQL. Дополнительные сведения о TDE с поддержкой подхода BYOK см. в статье [о прозрачном шифровании данных с поддержкой BYOK в Azure SQL](transparent-data-encryption-byok-azure-sql.md). 

## <a name="prerequisites-for-powershell"></a>Необходимые условия для использования PowerShell

- Требуется подписка Azure и права администратора этой подписки.
- [Рекомендуется, но необязательно] Наличие аппаратного модуля безопасности (HSM) или локального хранилища ключей для создания локальной копии материала ключа средства защиты TDE.
- Должна быть установлена и запущена служба Azure PowerShell версии 4.2.0 или более поздней. 
- Созданные Azure Key Vault и ключ для TDE.
   - [Инструкции по использованию PowerShell для Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started)
   - [Инструкции по использованию аппаратного модуля безопасности (HSM) и хранилища Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
- Ключ, используемый для прозрачного шифрования данных, должен иметь следующие характеристики:
   - быть бессрочным;
   - не быть отключенным;
   - иметь возможность выполнять операции *получения*, *упаковки ключа*, *распаковки ключа*.

## <a name="step-1-assign-an-azure-ad-identity-to-your-server"></a>Шаг 1. Назначение удостоверения Azure Active Directory серверу 

При наличии существующего сервера добавьте удостоверение Azure Active Directory на сервер, как показано ниже.

   ```powershell
   $server = Set-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -AssignIdentity
   ```

Если вы создаете сервер, используйте командлет [New-AzureRmSqlServer](/powershell/module/azurerm.sql/new-azurermsqlserver) с тегом -Identity, чтобы добавить удостоверение Azure Active Directory во время этого процесса:

   ```powershell
   $server = New-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -Location <RegionName> `
   -ServerName <LogicalServerName> `
   -ServerVersion "12.0" `
   -SqlAdministratorCredentials <PSCredential> `
   -AssignIdentity 
   ```

## <a name="step-2-grant-key-vault-permissions-to-your-server"></a>Шаг 2. Предоставление серверу разрешений на доступ к хранилищу Key Vault

С помощью командлета [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) предоставьте серверу доступ к хранилищу ключей перед использованием хранящегося в нем ключа для прозрачного шифрования данных.

   ```powershell
   Set-AzureRmKeyVaultAccessPolicy  `
   -VaultName <KeyVaultName> `
   -ObjectId $server.Identity.PrincipalId `
   -PermissionsToKeys get, wrapKey, unwrapKey
   ```

## <a name="step-3-add-the-key-vault-key-to-the-server-and-set-the-tde-protector"></a>Шаг 3. Добавление ключа из хранилища Key Vault на сервер и настройка средства защиты TDE

- С помощью командлета [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) добавьте ключ из хранилища Key Vault на сервер.
- С помощью командлета [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) задайте ключ в качестве средства защиты TDE для всех ресурсов сервера.
- С помощью командлета [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) проверьте, что средство защиты TDE настроено надлежащим образом.

> [!Note]
> Общая длина имени хранилища ключей и имени ключа не может превышать 94 символов.
> 

>[!Tip]
>Пример идентификатора KeyId из Key Vault: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
>

   ```powershell
   <# Add the key from Key Vault to the server #>
   Add-AzureRmSqlServerKeyVaultKey `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -KeyId <KeyVaultKeyId>

   <# Set the key as the TDE protector for all resources under the server #>
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> 

   <# To confirm that the TDE protector was configured as intended: #>
   Get-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> 
   ```

## <a name="step-4-turn-on-tde"></a>Шаг 4. Включение TDE 

С помощью командлета [Set-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) включите TDE.

   ```powershell
   Set-AzureRMSqlDatabaseTransparentDataEncryption `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName> `
   -State "Enabled"
   ```

Теперь для базы данных или хранилища данных включено прозрачное шифрование данных с помощью ключа шифрования в хранилище Key Vault.

## <a name="step-5-check-the-encryption-state-and-encryption-activity"></a>Шаг 5. Проверка состояния и активности шифрования

Воспользуйтесь командлетом [Get-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption), чтобы узнать состояние шифрования, и командлетом [Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity), чтобы проверить ход выполнения шифрования для базы данных или хранилища данных.

   ```powershell
   # Get the encryption state
   Get-AzureRMSqlDatabaseTransparentDataEncryption `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName> `

   <# Check the encryption progress for a database or data warehouse #>
   Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -DatabaseName <DatabaseName>  
   ```

## <a name="other-useful-powershell-cmdlets"></a>Другие полезные командлеты PowerShell

- Командлет [Set-AzureRMSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) используется для отключения TDE.

   ```powershell
   Set-AzureRMSqlDatabaseTransparentDataEncryption `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -DatabaseName <DatabaseName> `
   -State "Disabled”
   ```
 
- Командлет [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) используется для получения списка ключей хранилища Key Vault, добавленных на сервер.

   ```powershell
   <# KeyId is an optional parameter, to return a specific key version #>
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>
   ```
 
- Командлет [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) используется для удаления ключа Key Vault с сервера.

   ```powershell
   <# The key set as the TDE Protector cannot be removed. #>
   Remove-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>   
   ```
 
## <a name="troubleshooting"></a>Устранение неполадок

При возникновении ошибки проверьте следующие моменты.
- Если не удается найти хранилище ключей, проверьте, что вы используете правильную подписку, выполнив командлет [Get-AzureRmSubscription](/powershell/module/azurerm.profile/get-azurermsubscription).

   ```powershell
   Get-AzureRmSubscription `
   -SubscriptionId <SubscriptionId>
   ```

- Если не удается добавить новый ключ на сервер или новый ключ не может быть обновлен в качестве средства защиты TDE, проверьте следующие моменты.
   - Ключ не должен иметь срока действия.
   - Для ключа должны быть включены операции *получения*, *упаковки ключа* и *распаковки ключа*.

## <a name="next-steps"></a>Следующие шаги

- Узнайте, как заменить средство защиты TDE сервера в соответствии с требованиями безопасности: [Rotate the Transparent Data Encryption protector Using PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md) (Смена средства защиты прозрачного шифрования данных с помощью PowerShell).
- Узнайте, как удалить потенциально скомпрометированное средство защиты TDE в случае угрозы безопасности, изучив [эту статью](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md). 

## <a name="prerequisites-for-cli"></a>Необходимые условия для использования CLI

- Требуется подписка Azure и права администратора этой подписки.
- [Рекомендуется, но необязательно] Наличие аппаратного модуля безопасности (HSM) или локального хранилища ключей для создания локальной копии материала ключа средства защиты TDE.
- Интерфейс командной строки версии 2.0 или более поздней. Чтобы установить последнюю версию и подключиться к подписке Azure, см. статью [Установка и настройка кроссплатформенного интерфейса командной строки Azure 2.0](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest). 
- Созданные Azure Key Vault и ключ для TDE.
   - [Управление Key Vault с помощью CLI 2.0](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-manage-with-cli2)
   - [Инструкции по использованию аппаратного модуля безопасности (HSM) и хранилища Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
- Ключ, используемый для прозрачного шифрования данных, должен иметь следующие характеристики:
   - быть бессрочным;
   - не быть отключенным;
   - иметь возможность выполнять операции *получения*, *упаковки ключа*, *распаковки ключа*.
   
## <a name="step-1-create-a-server-and-assign-an-azure-ad-identity-to-your-server"></a>Шаг 1. Создание сервера и назначение ему удостоверения Azure Active Directory
      ```cli
      # create server (with identity) and database
      az sql server create -n "ServerName" -g "ResourceGroupName" -l "westus" -u "cloudsa" -p "YourFavoritePassWord99@34" -I 
      az sql db create -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 
      ```

 
## <a name="step-2-grant-key-vault-permissions-to-your-server"></a>Шаг 2. Предоставление серверу разрешений на доступ к хранилищу Key Vault
      ```cli
      # create key vault, key and grant permission
      az keyvault create -n "VaultName" -g "ResourceGroupName" 
      az keyvault key create -n myKey -p software --vault-name "VaultName" 
      az keyvault set-policy -n "VaultName" --object-id "ServerIdentityObjectId" -g "ResourceGroupName" --key-permissions wrapKey unwrapKey get list 
      ```

 
## <a name="step-3-add-the-key-vault-key-to-the-server-and-set-the-tde-protector"></a>Шаг 3. Добавление ключа из хранилища Key Vault на сервер и настройка средства защиты TDE
  
     ```cli
     # add server key and update encryption protector
      az sql server key create -g "ResourceGroupName" -s "ServerName" -t "AzureKeyVault" -u "FullVersionedKeyUri 
      az sql server tde-key update -g "ResourceGroupName" -s "ServerName" -t AzureKeyVault -u "FullVersionedKeyUri" 
      ```
  
  > [!Note]
> Общая длина имени хранилища ключей и имени ключа не может превышать 94 символов.
> 

>[!Tip]
>Пример идентификатора KeyId из Key Vault: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h
>
  
## <a name="step-4-turn-on-tde"></a>Шаг 4. Включение TDE 
      ```cli
      # enable encryption
      az sql db tde create -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" --status Enabled 
      ```

Теперь для базы данных или хранилища данных включено прозрачное шифрование данных с помощью ключа шифрования в хранилище Key Vault.

## <a name="step-5-check-the-encryption-state-and-encryption-activity"></a>Шаг 5. Проверка состояния и активности шифрования

     ```cli
      # get encryption scan progress
      az sql db tde show-activity -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 

      # get whether encryption is on or off
      az sql db tde show-configuration -n "DatabaseName" -g "ResourceGroupName" -s "ServerName" 

      ```
