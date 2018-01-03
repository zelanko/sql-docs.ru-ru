---
title: "Удаление средства защиты TDE с помощью PowerShell в Azure SQL | Документы Майкрософт"
description: "В этом практическом руководстве содержатся сведения о том, как действовать при наличии потенциально скомпрометированного средства защиты TDE для базы данных или хранилища данных SQL Azure, которое использует TDE с поддержкой BYOK."
keywords: 
services: sql-database
documentationcenter: 
author: becczhang
manager: craigg
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: 
ms.component: security
ms.workload: Inactive
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.openlocfilehash: 30b08c760eff3bdeb6d264d1c9d79c375f0a09ec
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="remove-a-transparent-data-encryption-tde-protector-using-powershell"></a>Удаление средства защиты прозрачного шифрования данных (TDE) с помощью PowerShell
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

## <a name="prerequisites"></a>предварительные требования
- Требуется подписка Azure и права администратора этой подписки.
- Должна быть установлена и запущена служба Azure PowerShell версии 4.2.0 или более поздней. 
- В этом практическом руководстве предполагается, что вы уже используете ключ из Azure Key Vault в качестве средства защиты TDE для базы данных или хранилища данных SQL Azure. Дополнительные сведения см. в статье [Transparent Data Encryption with BYOK Support](transparent-data-encryption-byok-azure-sql.md) (Прозрачное шифрование данных с поддержкой BYOK).

## <a name="overview"></a>Обзор
В этом руководстве содержатся сведения о том, как действовать при наличии потенциально скомпрометированного средства защиты TDE для базы данных или хранилища данных SQL Azure, которое использует TDE с поддержкой BYOK. Дополнительные сведения о поддержке BYOK для TDE см. на [странице общих сведений](transparent-data-encryption-byok-azure-sql.md). 

Следующие процедуры следует выполнять только в крайних случаях или в тестовой среде. Внимательно ознакомьтесь с практическим руководством, поскольку удаление активно используемых средств защиты TDE из Azure Key Vault может привести к **потере данных**. 

Если относительно ключа есть подозрение, что он скомпрометирован, например, у службы или пользователя мог быть несанкционированный доступ к ключу, рекомендуется удалить ключ.

Необходимо помнить, что после удаления средства защиты TDE в хранилище Key Vault **блокируются все подключения к зашифрованным базам данных для сервера и эти базы данных переходят в автономный режим и удаляются в течение 24 часов**. Старые резервные копии, зашифрованные с помощью скомпрометированного ключа, становятся недоступными.

В этом руководстве рассматриваются два подхода в зависимости от нужного результата после реагирования на инцидент:
- Обеспечение **доступности** баз данных и хранилищ данных SQL Azure
- **Ограничение доступности** баз данных и хранилищ данных SQL Azure

## <a name="to-keep-the-encrypted-resources-accessible"></a>Обеспечение доступности зашифрованных ресурсов
1. Создайте [ключ в хранилище Key Vault](https://docs.microsoft.com/powershell/module/azurerm.keyvault/add-azurekeyvaultkey?view=azurermps-4.1.0). Убедитесь, что этот новый ключ создается в хранилище, отдельном от потенциально скомпрометированного средства защиты TDE, так как управление доступом предоставляется на уровне хранилища. 
2. Добавьте новый ключ на сервер с помощью командлетов [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) и [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) и обновите его как новое средство защиты TDE сервера.

   ```powershell
   # Add the key from Key Vault to the server  
   Add-AzureRmSqlServerKeyVaultKey `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -KeyId <KeyVaultKeyId>
   
   # Set the key as the TDE protector for all resources under the server
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ResourceGroupName <SQLDatabaseResourceGroupName> `
   -ServerName <LogicalServerName> `
   -Type AzureKeyVault -KeyId <KeyVaultKeyId> 
   ```

3. Убедитесь, что сервер и все реплики были обновлены до нового средства защиты TDE с помощью командлета [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector). 

   >[!NOTE]
   > Распространение нового средства защиты TDE на все базы данных и базы данных-получатели на сервере может занять несколько минут.
   >

   ```powershell
   Get-AzureRmSqlServerTransparentDataEncryptionProtector `
   -ServerName <LogicalServerName> `
   -ResourceGroupName <SQLDatabaseResourceGroupName>
   ```

4. Создайте [резервную копию нового ключа](/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey) в хранилище Key Vault.

   ```powershell
   <# -OutputFile parameter is optional; 
   if removed, a file name is automatically generated. #>
   Backup-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -OutputFile <DesiredBackupFilePath>
   ```
 
5. Удалите скомпрометированный ключ из хранилища Key Vault с помощью командлета [Remove-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/remove-azurekeyvaultkey). 

   ```powershell
   Remove-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName>
   ```
 
6. Чтобы восстановить ключ в Key Vault в будущем, выполните командлет [Restore-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/restore-azurekeyvaultkey):
   ```powershell
   Restore-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -InputFile <BackupFilePath>
   ```
 
## <a name="to-make-the-encrypted-resources-inaccessible"></a>Ограничение доступности зашифрованных ресурсов
1. Удалите базы данных, которые зашифрованы с помощью возможно скомпрометированного ключа.
Файлы базы данных и журнала автоматически архивируются, поэтому восстановление базы данных на определенный момент можно выполнить в любое время (при условии, что вы указали ключ). Базы данных должны быть удалены перед удалением действующего средства защиты TDE, чтобы избежать потери данных за 10 минут самой последней транзакции. 
2. Создайте резервную копию материала ключа средства защиты TDE в Key Vault.
3. Удалите возможно скомпрометированный ключ из хранилища Key Vault.

## <a name="next-steps"></a>Следующие шаги

- Узнайте, как заменить средство защиты TDE сервера в соответствии с требованиями безопасности: [Rotate the Transparent Data Encryption protector Using PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md) (Смена средства защиты прозрачного шифрования данных с помощью PowerShell).

- Начините использовать поддержку BYOK для TDE: [Turn on TDE using your own key from Key Vault using PowerShell](transparent-data-encryption-byok-azure-sql-configure.md) (Включение TDE с использованием собственного ключа из Key Vault с помощью PowerShell).
