---
title: Смена средства защиты TDE с помощью PowerShell в Azure SQL | Документы Майкрософт
description: Сведения о смене средства защиты прозрачного шифрования данных (TDE) на сервере Azure SQL.
keywords: ''
services: sql-database
documentationcenter: ''
author: becczhang
manager: jhubbard
editor: ''
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: ''
ms.component: security
ms.tgt_pltfrm: ''
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: ryzhang26
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: cee667b6f92c19c03cd670537d09dc5ccc7b03f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32619275"
---
# <a name="rotate-the-transparent-data-encryption-tde-protector-using-powershell"></a>Смена средства защиты прозрачного шифрования данных (TDE) с помощью PowerShell 
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

В этом практическом руководстве описывается процедура смены ключа сервера Azure SQL с помощью средства защиты TDE из Azure Key Vault. Смена средства защиты TDE для сервера Azure SQL означает переключение на новый асимметричный ключ, который защищает базы данных на сервере. Смена ключа выполняется в оперативном режиме и обычно занимает несколько секунд, так как при этом происходят лишь расшифровка и повторное шифрование шифрования данных для базы данных, а не всей базы данных.

В этом руководстве рассматривается два варианта смены средства защиты TDE на сервере.

> [!NOTE]
> Перед сменой ключа необходимо возобновить работу приостановленного хранилища данных SQL.
>

> [!IMPORTANT]
> **Не удаляйте** предыдущие версии ключа после смены.  При смене ключей некоторые данные по-прежнему шифруются с помощью предыдущих ключей, например старые резервные копии базы данных. 
>

## <a name="prerequisites"></a>предварительные требования

- В этом практическом руководстве предполагается, что вы уже используете ключ из Azure Key Vault в качестве средства защиты TDE для базы данных или хранилища данных SQL Azure. Дополнительные сведения см. в статье [Transparent Data Encryption with BYOK Support](transparent-data-encryption-byok-azure-sql.md) (Прозрачное шифрование данных с поддержкой BYOK).
- Должна быть установлена и запущена служба Azure PowerShell версии 3.7.0 или более поздней. 
- [Рекомендуется, но необязательно] Сначала создайте материал ключа для средства защиты TDE в аппаратном модуле безопасности (HSM) или локальном хранилище ключей, а затем импортируйте этот материал в Azure Key Vault. Следуйте [инструкциям по использованию аппаратного модуля безопасности (HSM) и хранилища Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started).

## <a name="option-1-auto-rotation"></a>Вариант 1. Автоматическая смена

Создайте новую версию существующего ключа средства защиты TDE в ключа в хранилище Key Vault с тем же именем ключа и хранилища ключей. Служба Azure SQL начнет использовать эту новую версию в течение 24 часов. 

Чтобы создать новую версию средства защиты TDE, используйте командлет [Add-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/add-azurekeyvaultkey):

   ```powershell
   Add-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -Destination <HardwareOrSoftware>
   ```

## <a name="option-2-manual-rotation"></a>Вариант 2. Смена вручную

В этом случае используются командлеты [Add-AzureKeyVaultKey](/powershell/module/azurerm.keyvault/add-azurekeyvaultkey), [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) и [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) для добавления совершенно нового ключа, который может иметь новое имя или находиться в другом хранилище ключей. 

>[!NOTE]
>Общая длина имени хранилища ключей и имени ключа не может превышать 94 символов.
>

   ```powershell
   # Add a new key to Key Vault
   Add-AzureKeyVaultKey `
   -VaultName <KeyVaultName> `
   -Name <KeyVaultKeyName> `
   -Destination <HardwareOrSoftware>

   # Add the new key from Key Vault to the server
   Add-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>   
  
   <# Set the key as the TDE protector for all resources 
   under the server #>
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
  
## <a name="other-useful-powershell-cmdlets"></a>Другие полезные командлеты PowerShell

- Чтобы переключить режим средства защиты TDE с управления Майкрософт на BYOK, выполните командлет [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector).

   ```powershell
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type AzureKeyVault `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```

- Чтобы переключить режим средства защиты TDE с BYOK на управление Майкрософт, выполните командлет [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector).

   ```powershell
   Set-AzureRmSqlServerTransparentDataEncryptionProtector `
   -Type ServiceManaged `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName> 
   ``` 

## <a name="next-steps"></a>Следующие шаги

- Узнайте, как удалить потенциально скомпрометированное средство защиты TDE в случае угрозы безопасности, изучив [эту статью](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md). 

- Начините использовать поддержку BYOK для TDE: [Turn on TDE using your own key from Key Vault using PowerShell](transparent-data-encryption-byok-azure-sql-configure.md) (Включение TDE с использованием собственного ключа из Key Vault с помощью PowerShell).
