---
title: "Включение прозрачного шифрования данных с использованием собственного ключа Azure Key Vault с помощью PowerShell | Документы Майкрософт"
description: "Сведения о настройке базы данных и хранилища данных SQL Azure для использования прозрачного шифрования данных (TDE) для шифрования хранящихся данных с помощью PowerShell."
keywords: 
documentationcenter: 
author: aliceku
manager: craigg
editor: 
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.component: security
ms.workload: On Demand
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: aliceku
ms.openlocfilehash: 0acfd9faa668d1e86cb82496bdd97dc6a0ec2bc8
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="powershell-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vault"></a>Включение прозрачного шифрования данных с использованием собственного ключа из Azure Key Vault с помощью PowerShell
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

В этом практическом руководстве рассматриваются способы использования ключа из Azure Key Vault для прозрачного шифрования данных (TDE) в базе данных или хранилище данных SQL. Дополнительные сведения о TDE с поддержкой подхода BYOK см. в статье [о прозрачном шифровании данных с поддержкой BYOK в Azure SQL](transparent-data-encryption-byok-azure-sql.md). 

## <a name="prerequisites"></a>предварительные требования

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

## <a name="step-1-assign-an-aad-identity-to-your-server"></a>Шаг 1. Назначение удостоверения AAD серверу 

При наличии существующего сервера добавьте удостоверение AAD на сервер, как показано ниже.

   ```powershell
   $server = Set-AzureRmSqlServer `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -AssignIdentity
   ```

Если вы создаете сервер, используйте командлет [New-AzureRmSqlServer](/powershell/module/azurerm.sql/new-azurermsqlserver) с тегом -Identity, чтобы добавить удостоверение во время этого процесса:

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
>Пример KeyId из Key Vault: https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h.
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

## <a name="step-5-check-the-encryption-state-and-encryption-activity-of-the-database-or-data-warehouse"></a>Шаг 5. Проверьте состояние шифрования и действие шифрования базы данных или хранилища данных

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


