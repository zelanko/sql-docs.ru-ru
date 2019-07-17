---
title: Распространенные ошибки с прозрачным шифрованием данных (TDE) с использованием управляемых клиентом ключей в Azure Key Vault | Документация Майкрософт
description: Устранение неполадок с прозрачным шифрованием данных (TDE) с использованием конфигурации Azure Key Vault.
helpviewer_keywords:
- troublshooting, tde akv
- tde akv configuration, troubleshooting
- tde troubleshooting
author: aliceku
manager: craigg
ms.prod: sql
ms.technology: security
ms.reviewer: vanto
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: aliceku
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f963e15d674115029fce78b98ba280fe75da2cd1
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716666"
---
# <a name="common-errors-for-transparent-data-encryption-with-customer-managed-keys-in-azure-key-vault"></a>Распространенные ошибки с прозрачным шифрованием данных (TDE) с использованием управляемых клиентом ключей в Azure Key Vault

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
В статье описаны требования к использованию прозрачного шифрования данных (TDE) с использованием управляемых клиентом ключей в Azure Key Vault и способы определения и устранения распространенных ошибок.

## <a name="requirements"></a>Требования

Чтобы устранить неполадки с TDE с использованием средства защиты TDE в Key Vault, необходимо выполнить следующие условия:

- Экземпляр логического сервера SQL и хранилище ключей должны находиться в одном регионе.
- Удостоверение экземпляра логического сервера SQL, предоставленное Azure Active Directory (AppId в Azure Key Vault), должно быть клиентом в исходной подписке. Если сервер был перемещен в другую подписку из той, в которой он был создан, удостоверение сервера (AppId) нужно создать заново.
- Хранилище ключей должно быть запущено. Сведения о том, как проверить состояние хранилища ключей, см. в статье о [работоспособности ресурсов Azure](https://docs.microsoft.com/azure/service-health/resource-health-overview). Чтобы зарегистрироваться для получения уведомлений, ознакомьтесь со сведениями о [группах действий](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups).
- В сценариях геоизбыточного аварийного восстановления оба хранилища ключей должны содержать одинаковый ключ для успешной отработки отказа.
- Логический сервер должен иметь удостоверение Azure AD (AppId) для аутентификации в хранилище ключей.
- Для AppId нужно предоставить доступ к хранилищу ключей и разрешение на получение, упаковку и распаковку ключей, которые выбраны в качестве средства защиты TDE.

Дополнительные сведения см. в рекомендациях по [настройке TDE с использованием Azure Key Vault](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault).

## <a name="common-misconfigurations"></a>Распространенные неправильные конфигурации

Большинство проблем, возникающих при использовании TDE с Key Vault, вызваны одной из следующих ошибок конфигурации:

### <a name="the-key-vault-is-unavailable-or-doesnt-exist"></a>Хранилище ключей недоступно или не существует.

- Хранилище ключей случайно удалено.
- Брандмауэр разрешает доступ к Azure Key Vault, но запрещает доступ к службам Майкрософт.

### <a name="no-permissions-to-access-the-key-vault-or-the-key-doesnt-exist"></a>Нет разрешения на доступ к хранилищу ключей или ключ не существует.

- Ключ случайно удален.
- Удостоверение AppId экземпляра логического сервера SQL Server случайно удалено.
- Экземпляр логического сервера SQL Server перемещен в другую подписку. Если логический сервер был перемещен в другую подписку, необходимо создать новое удостоверение AppId.
- Предоставленные для AppId разрешения использовать ключи являются недостаточными (не позволяют получать, упаковывать и распаковывать ключи).
- Разрешения для AppId экземпляра логического сервера SQL Server были отозваны.

## <a name="identify-and-resolve-common-errors"></a>Определение и исправление распространенных ошибок

В этом разделе перечислены действия по устранению распространенных ошибок.

### <a name="missing-server-identity"></a>Отсутствует идентификатор сервера

**Сообщение об ошибке**

_401 AzureKeyVaultNoServerIdentity. Удостоверение сервера неправильно настроено на сервере. Обратитесь в службу поддержки._

**Обнаружение**

Чтобы убедиться, что удостоверение было назначено экземпляру логического сервера SQL Server, используйте следующие командлет или команду:

- Azure PowerShell: [Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 

- Azure CLI: [az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

**Исправление**

Чтобы настроить удостоверение Azure AD (AppId), используйте следующие командлет или команду для экземпляра логического SQL Server:

- Azure PowerShell: [Set-AzureRmSqlServer](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0) с параметром `-AssignIdentity`.

- Azure CLI: [az sql server update](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update) с параметром `--assign_identity`.

На портале Azure перейдите в хранилище ключей и выберите **Политики доступа**. Выполните следующие действия: 

 1. Нажмите кнопку **Добавить**, чтобы добавить AppId для сервера, созданного на предыдущем шаге. 
 1. Назначьте следующие разрешения ключей: Get, Wrap и Unwrap 

Дополнительные сведения см. в руководстве по [назначению серверу удостоверения Azure Active Directory](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server).

> [!IMPORTANT]
> Если экземпляр логического сервера SQL Server был перемещен в другую подписку после начальной настройки TDE с Key Vault, шаг настройки удостоверения AAD следует повторить, чтобы создать новое удостоверение AppId. Затем добавьте AppId в хранилище ключей и назначьте правильные разрешения для ключа. 
>

### <a name="missing-key-vault"></a>Отсутствующее хранилище ключей

**Сообщение об ошибке**

_503 AzureKeyVaultConnectionFailed. Операцию не удалось завершить на сервере, так как не удалось подключиться к Azure Key Vault._

**Обнаружение**

Чтобы определить URI ключа и хранилище ключей, сделайте следующее:

1. Чтобы получить URI ключа на определенном экземпляре логического сервера SQL Server, используйте следующие командлет или команду:

    - Azure PowerShell: [Get-AzureRmSqlServerKeyVaultKey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

    - Azure CLI: [az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

1. Используйте URI ключа для идентификации хранилища ключей:

    - Azure PowerShell: можно изучить свойства переменной $MyServerKeyVaultKey, чтобы получить сведения о хранилище ключей.

    - Azure CLI: проверьте полученное средство защиты шифрования сервера на наличие сведений о хранилище ключей.

**Исправление**

Убедитесь, что хранилище ключей доступно:

- Убедитесь, что хранилище ключей доступно и что экземпляр логического сервера SQL Server имеет к нему доступ.
- Если хранилище ключей защищено брандмауэром, убедитесь, что установлен флажок, разрешающий службам Майкрософт доступ к хранилищу ключей.
- Если хранилище ключей было случайно удалено, настройку следует повторить с самого начала.


### <a name="missing-key"></a>Отсутствует ключ

**Сообщения об ошибках**

_404 ServerKeyNotFound. Запрашиваемый ключ сервера не найден в текущей подписке._ 

_409 ServerKeyDoesNotExists. Ключ сервера не существует._

**Обнаружение**

Чтобы определить URI ключа и хранилище ключей, сделайте следующее:

- Чтобы получить URI ключа, добавленного к экземпляру логического сервера SQL Server, используйте следующие командлет или команду в [отсутствующем хранилище ключей](#missing-key-vault): Эти команды возвращают список ключей.

**Исправление**

Убедитесь, что средство защиты TDE присутствует в Key Vault:

1. Определите хранилище ключей и перейдите к нему на портале Azure.
1. Убедитесь, что ключ, определенный по URI ключа, присутствует.

### <a name="missing-permissions"></a>Отсутствуют разрешения

**Сообщение об ошибке**

_401 AzureKeyVaultMissingPermissions. У сервера отсутствуют необходимые разрешения для Azure Key Vault._

**Обнаружение**

Чтобы определить URI ключа и хранилище ключей, сделайте следующее: 

- Чтобы определить хранилище ключей, которое использует экземпляр логического сервера SQL Server, используйте следующие командлет или команду в [отсутствующем хранилище ключей](#missing-key-vault).

**Исправление**

Убедитесь, что экземпляр логического сервера SQL Server имеет разрешения в хранилище ключей и необходимые разрешения для доступа к ключу.

- На портале Azure перейдите в хранилище ключей и выберите **Политики доступа**. Найдите AppId экземпляра логического сервера SQL Server.  
- Если удостоверение AppId присутствует, убедитесь, что оно имеет следующие основные разрешения: Get, Wrap и Unwrap.
- Если AppId отсутствует, добавьте его с помощью кнопки **Добавить**. 

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения см. в рекомендациях по [настройке TDE с использованием Azure Key Vault](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault).
- См. дополнительные сведения о [работоспособности ресурсов Azure](https://docs.microsoft.com/azure/service-health/resource-health-overview).
- См. сведения о том, как [назначить серверу удостоверение Azure AD](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server).
