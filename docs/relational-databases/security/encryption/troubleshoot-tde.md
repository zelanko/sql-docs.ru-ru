---
title: Распространенные ошибки с прозрачным шифрованием данных (TDE) с помощью управляемых клиентом ключей и способы их устранения в Azure Key Vault (AKV) | Документация Майкрософт
description: Устранение неполадок в прозрачном шифровании данных (TDE) с конфигурацией Azure Key Vault.
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
ms.openlocfilehash: 1366d0a20ed39b466d1a2f6cb3e84f0f30e17f9f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718086"
---
# <a name="common-errors-and-resolutions-with-transparent-data-encryption-tde-with-customer-managed-keys-in-azure-key-vault-akv"></a>Распространенные ошибки с прозрачным шифрованием данных (TDE) с управляемыми клиентом ключами и способы их устранения в Azure Key Vault (AKV)

[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md.md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]
Этот подраздел содержит следующие сведения:  
  
- Требования  
- Как определить и устранить наиболее распространенные ошибки

## <a name="requirements"></a>Требования
Для устранения неполадок [прозрачного шифрования данных с помощью управляемых пользователем средств защиты TDE в конфигурации AKV](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql#guidelines-for-configuring-tde-with-azure-key-vault) начнем с подтверждения следующих требований:
- Логический сервер SQL и хранилище ключей должны находиться в одном регионе.
- Логическое удостоверение сервера SQL, предоставленное Azure Active Directory (APPID в хранилище Azure Key Vault), ограничено клиентом в исходной подписке.  Если сервер был перемещен в другую подписку, удостоверение сервера (APPID) следует создать заново.
- Хранилище ключей необходимо настроить настройку и запустить; см. сведения о [работоспособности ресурсов Azure](https://docs.microsoft.com/azure/service-health/resource-health-overview), чтобы проверить состояние хранилища ключей, и раздел [Группы действий](https://docs.microsoft.com/azure/azure-monitor/platform/action-groups), чтобы подписаться на уведомления.
- В сценарии географического аварийного восстановления оба хранилища ключей должны содержать материал ключа для успешной отработки отказа.
- Логический сервер должен иметь удостоверение Azure Active Directory (AAD) (APPID) для проверки подлинности в хранилище ключей.
- APPID должен иметь доступ к хранилищу ключей и упаковки, распаковки и получения разрешения на доступ к ключам, которые выбраны в качестве средства защиты TDE.

Большинство проблем, возникающих при использовании прозрачного шифрования данных с AKV, возникает из-за одной из следующих ошибок конфигурации:

### <a name="key-vault-unavailable-or-doesnt-exist"></a>Хранилище ключей недоступно или не существует?
- Хранилище ключей случайно удалено
- Брандмауэр хранилища Azure Key Vault запрещает доступ к службам Майкрософт

### <a name="no-permissions-to-access-the-key-vault-or-key-doesnt-exist"></a>Нет разрешения на доступ к хранилищу ключей или ключ не существует?
- Ключ случайно удален
- SQL APPID случайно удален
- SQL был перемещен в другую подписку, которой требуется новый код APPID
- Разрешения, предоставленные APPID для ключей, недостаточны (упаковка, распаковка, получение доступа)
- Разрешения для SQL APPID отозваны


В следующем разделе перечислены действия по устранению неполадок для наиболее распространенных ошибок.


## <a name="how-to-identify-and-resolve-the-most-common-errors"></a>Как определить и устранить наиболее распространенные ошибки

## <a name="missing-server-identity"></a>Отсутствует идентификатор сервера
Сообщение об ошибке. "401 AzureKeyVaultNoServerIdentity — удостоверение сервера неправильно настроено на сервере. Обратитесь в службу поддержки".

Обнаружение. Чтобы убедиться, что удостоверение было назначено логическому серверу SQL, используйте следующую команду:

- [Azure PowerShell Get-AzureRMSqlServer](https://docs.microsoft.com/powershell/module/AzureRM.Sql/Get-AzureRmSqlServer?view=azurermps-6.13.0) 
- [Azure CLI az-sql-server-show](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-show)

Устранение рисков. Настройте удостоверение Azure Active Directory (Azure AD) (APPID) для логического сервера SQL

Для PowerShell: Используйте команду Set-AzureRmSqlServer с параметром [-AssignIdentity](https://docs.microsoft.com/powershell/module/azurerm.sql/set-azurermsqlserver?view=azurermps-6.13.0) 

Для интерфейса командной строки: Используйте команду az sql server update с параметром [--assign_identity](https://docs.microsoft.com/cli/azure/sql/server?view=azure-cli-latest#az-sql-server-update) 

На портале Azure перейдите в хранилище ключей и выберите политики доступа:  
 - Используя кнопку "Добавить", добавьте для сервера APPID, созданный на предыдущем шаге. 
 - Назначьте следующие разрешения ключей: Get, Wrap и Unwrap 

[Дополнительные сведения](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql-configure?view=sql-server-2017&viewFallbackFrom=azuresqldb-current#step-1-assign-an-azure-ad-identity-to-your-server)

> [!IMPORTANT]
> Если логический сервер SQL был перемещен в новую подписку после начальной настройки TDE с AKV, то шаг настройки удостоверения AAD следует повторить для создания нового APPID.  Новый код APPID затем следует добавить в хранилище ключей,а также повторно назначить ему правильные разрешения. 
>

## <a name="missing-key-vault"></a>Отсутствующее хранилище ключей
Сообщение об ошибке: "503 AzureKeyVaultConnectionFailed — операцию не удалось завершить на сервере, так как не удалось подключиться к хранилищу Azure Key Vault".

Обнаружение. Как определить URI ключа и хранилища ключей 

Шаг 1. Для получения URI ключа на определенном логическом сервере SQL используйте следующую команду:

-[Azure PowerShell get-azurermsqlserverkeyvaultkey](https://docs.microsoft.com/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey?view=azurermps-6.13.0)

-[Azure CLI az-sql-server-tde-key-show](https://docs.microsoft.com/cli/azure/sql/server/tde-key?view=azure-cli-latest#az-sql-server-tde-key-show) 

Шаг 2. Используйте URI ключа для идентификации хранилища ключей

PowerShell. Можно проверить свойства $MyServerKeyVaultKey для получения сведений о хранилище ключей

Интерфейс командной строки. Проверьте возвращенное средство защиты шифрования сервера на наличие сведений о хранилище ключей

Устранение рисков. Убедитесь, что хранилище ключей доступно
- Убедитесь, что хранилище ключей доступно для логического сервера SQL
- Если хранилище ключей находится за брандмауэром, убедитесь, что установлен флажок, разрешающий службам Майкрософт доступ к хранилищу ключей
- Если хранилище ключей было случайно удалено, настройку следует повторить с самого начала


## <a name="missing-key"></a>Отсутствует ключ 
Сообщение об ошибке: "404 ServerKeyNotFound — запрашиваемый ключ сервера не найден в текущей подписке".
"409 ServerKeyDoesNotExists — ключ сервера не существует".

Обнаружение. Как определить URI ключа и хранилища ключей
- Определите URI ключа, добавленного к логическому серверу SQL, с использованием командлетов для получения списка ключей из раздела "Отсутствующее хранилище ключей" выше.

Устранение рисков. Убедитесь, что средство защиты прозрачного шифрования данных присутствует в AKV
- Определите хранилище ключей и перейдите к нему на портале Azure
- Убедитесь, что ключ, указанный по URI ключа, существует

## <a name="missing-permissions"></a>Отсутствуют разрешения 
Сообщение об ошибке: "401 AzureKeyVaultMissingPermissions — у сервера отсутствуют необходимые разрешения для Azure Key Vault".

Обнаружение. Как определить URI ключа и хранилища ключей
- Определите хранилище ключей, используемое логическим сервером SQL, с использованием командлетов из раздела "Отсутствующее хранилище ключей" выше.

Устранение рисков. Убедитесь, что логический сервер имеет разрешения в хранилище ключей и необходимые разрешения для доступа к ключу.
- На портале Azure перейдите в хранилище ключей и выберите политики доступа; найдите APPID SQL Server.  
  - Если APPID отсутствует, добавьте его с помощью кнопки "Добавить". 
  - Если APPID присутствует, убедитесь, что он имеет следующие основные разрешения: Get, Wrap и Unwrap.
