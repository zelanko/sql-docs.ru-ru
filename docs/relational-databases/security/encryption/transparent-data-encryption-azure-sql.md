---
title: "TDE для базы данных и хранилища данных SQL Azure | Документы Майкрософт"
description: "Общие сведения о прозрачном шифровании данных для базы данных и хранилища данных SQL. В этом документе описываются его преимущества и параметры конфигурации, включая прозрачное шифрование данных, управляемое службой, и создание собственных ключей."
keywords: 
author: becczhang
manager: craigg
editor: 
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.component: security
ms.custom: 
ms.workload: On Demand
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.openlocfilehash: 39e1807178f536a1bac2148deae406b1e3bb44b5
ms.sourcegitcommit: 34d3497039141d043429eed15d82973b18ad90f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2018
---
# <a name="transparent-data-encryption-for-azure-sql-database-and-data-warehouse"></a>Прозрачное шифрование данных для базы данных и хранилища данных SQL Azure
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

Прозрачное шифрование данных (TDE) позволяет защитить базу данных и хранилище данных SQL Azure от угрозы вредоносных действий, в реальном времени выполняя шифрование и расшифровку неактивной базы данных, связанных с ней резервных копий и файлов журнала транзакций. При этом изменение приложения не требуется.

TDE шифрует пространство хранения всей базы данных, используя симметричный ключ, который называется ключом шифрования базы данных. Ключ шифрования базы данных защищается средством защиты TDE и представляет собой либо управляемый службой сертификат (TDE, управляемое службой), либо асимметричный ключ, хранящийся в Azure Key Vault (создание собственных ключей). Средство защиты TDE настраивается на уровне сервера. 

При запуске базы данных зашифрованный ключ DEK расшифровывается, а затем используется для расшифровки и повторного шифрования файлов базы данных в процессе SQL Engine. Функция TDE выполняет шифрование и расшифровку ввода-вывода данных в реальном времени на уровне страницы. Каждая страница расшифровывается при считывании в память и шифруется перед записью на диск. Общее описание TDE см. в статье [Прозрачное шифрование данных (TDE)](transparent-data-encryption.md).

SQL Server, запущенный на виртуальной машине Azure, может также использовать асимметричный ключ из Key Vault. При этом этапы настройки будут не такими, как при использовании асимметричного ключа в базе данных SQL Azure. Дополнительные сведения см. в статье [Расширенное управление ключами с помощью Azure Key Vault (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md).

## <a name="service-managed-tde"></a>TDE, управляемое службой

В Azure параметр по умолчанию для TDE означает, что для защиты ключа шифрования базы данных используется встроенный сертификат сервера. Встроенный сертификат уникален для каждого сервера. Если база данных находится в отношении георепликации, первичная база данных и вторичная база данных с георепликацией защищаются ключом родительского сервера первичной базы данных. Если две базы данных подключены к одному серверу, используется один встроенный сертификат. Майкрософт автоматически меняет эти сертификаты каждые 90 дней.

Кроме того, Майкрософт прозрачно перемещает и администрирует ключи, когда это требуется для георепликации и восстановления. 

> [!IMPORTANT]
> По умолчанию все создаваемые базы данных SQL шифруются с использованием TDE, управляемого службой. Базы данных, существовавшие до мая 2017 года, и базы данных, созданные путем восстановления, георепликации и копирования, по умолчанию не шифруются.
>

## <a name="bring-your-own-key-preview"></a>Создание собственных ключей (предварительная версия)

Создание собственных ключей (BYOK, предварительная версия), позволяет пользователю управлять ключами шифрования TDE и контролировать, кто и когда может получать к ним доступ. Azure Key Vault (AKV) — это облачная внешняя система управления ключами Azure, которая является первой службой управления ключами, интегрированной с TDE для поддержки сценариев BYOK. Благодаря BYOK ключ шифрования базы данных защищается асимметричным ключом, хранящимся в AKV. Асимметричный ключ никогда не покидает Key Vault. Как только сервер получает разрешения для хранилища ключей, он отправляет к нему базовые запросы основных операций с ключами через службу Key Vault. Асимметричный ключ задается на уровне сервера и наследуется всеми базами данных на этом сервере. Благодаря поддержке BYOK пользователи могут выполнять задачи управления ключами, включая смену ключей, разрешения хранилища ключей, удаление ключей и включение проверки всех ключей шифрования или формирования связанных с ними отчетов. Key Vault обеспечивает централизованное управление ключами, предоставляет тщательно отслеживаемые аппаратные модули безопасности (HSM) и позволяет разделить управление ключами и данными для выполнения законодательных норм. Дополнительные сведения о хранилище ключей см. на [странице документации по хранилищу ключей](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).

Дополнительные сведения о TDE с поддержкой BYOK для базы данных и хранилища данных Azure SQL см. в статье [Прозрачное шифрование данных с поддержкой создания собственных ключей](transparent-data-encryption-byok-azure-sql.md).

Инструкции по началу работы с TDE с поддержкой BYOK см. в руководстве [Включение прозрачного шифрования данных с использованием собственного ключа из хранилища ключей с помощью PowerShell](transparent-data-encryption-byok-azure-sql-configure.md).

## <a name="moving-a-tde-protected-database"></a>Перемещение базы данных, защищаемой прозрачным шифрованием

Расшифровывать базы данных для работы в Azure не нужно. Параметры TDE базы данных-источника прозрачно наследуются целевым объектом. Сюда входят операции, связанные с:
- геовосстановлением;
- самостоятельным восстановлением до точки во времени;
- восстановлением удаленной базы данных;
- активной георепликацией;
- созданием копии базы данных.

При экспорте базы данных, защищаемой прозрачным шифрованием, экспортируемое содержимое базы данных не шифруется. Экспортированное содержимое хранится в незашифрованных файлах BACPAC. Не забудьте защитить файлы BACPAC соответствующим образом и включить TDE после завершения импорта новой базы данных.

Например, если файл BACPAC экспортируется из локальной версии SQL Server, то импортированное содержимое новой базы данных не шифруется автоматически. Точно так же новая база данных автоматически не шифруется при экспорте файла BACPAC в локальную версию SQL Server.

Единственное исключение — экспорт в базу данных SQL Azure или из нее. TDE в новой базе данных включено, но сам файл PACPAC по-прежнему не шифруется.

## <a name="managing-transparent-data-encryption-in-the-azure-portal"></a>Управление прозрачным шифрованием данных на портале Azure

Чтобы настроить TDE через портал Azure, нужно подключиться в качестве владельца Azure, участника или диспетчера безопасности SQL. 

Прозрачное шифрование данных задается на уровне базы данных. Чтобы включить TDE в базе данных, войдите на [портал Azure](https://portal.azure.com) с помощью учетной записи администратора или участника Azure. Найдите параметры TDE для своей пользовательской базы данных. По умолчанию используется TDE, управляемое службой, а сертификат TDE автоматически создается для сервера, содержащего базу данных. 

![прозрачное шифрование данных, управляемое службой](./media/transparent-data-encryption-azure-sql/service-managed-tde.png)  

Главный ключ TDE, который также называется *средством защиты TDE*, задается на уровне сервера. Чтобы использовать TDE с поддержкой создания собственных ключей и защитить базы данных с помощью ключа из Azure Key Vault, откройте параметры прозрачного шифрования данных для своего сервера. 

![прозрачное шифрование данных с поддержкой BYOK](./media/transparent-data-encryption-azure-sql/tde-byok-support.png) 

## <a name="managing-transparent-data-encryption-using-powershell"></a>Управление прозрачным шифрованием данных с помощью PowerShell

Для настройки TDE с помощью PowerShell нужно подключиться в качестве владельца Azure, участника или диспетчера безопасности SQL. 

| Командлет | Description |
| --- | --- |
| [Set-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) |Включает или отключает прозрачное шифрование данных для базы данных.|
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) |Получает состояние прозрачного шифрования данных для базы данных. |
| [Get-Azure-Rm-Sql-Database-Transparent-Data-Encryption-Activity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) |Проверяет ход шифрования базы данных. |
| [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) |Добавляет ключ Key Vault в SQL Server. |
| [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) |Получает ключи Key Vault для SQL Server. |
| [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) |Задает средство защиты TDE для SQL Server. |
| [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) |Получает средство защиты прозрачного шифрования данных. |
| [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) |Удаляет ключ Key Vault из SQL Server. |
|  | |

## <a name="managing-transparent-data-encryption-using-transact-sql"></a>Управление прозрачным шифрованием данных с помощью Transact-SQL

Подключитесь к базе данных, используя учетные данные администратора или участника роли **dbmanager** в базе данных master.

| Command | Description |
| --- | --- |
| [ALTER DATABASE (база данных Azure SQL)](/sql/t-sql/statements/alter-database-azure-sql-database) | Для шифрования и расшифровки базы данных используйте параметр SET ENCRYPTION ON/OFF. |
| [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) |Возвращает сведения о состоянии шифрования базы данных и о связанных ключах шифрования базы данных. |
| [sys.dm_pdw_nodes_database_encryption_keys](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql) |Возвращает сведения о состоянии шифрования каждого узла хранилища данных и о связанных ключах шифрования базы данных. | 
|  | |

Средство защиты TDE нельзя переключить на ключ из Azure Key Vault с помощью Transact-SQL; для этого нужно использовать PowerShell или портал Azure.

## <a name="managing-transparent-data-encryption-using-rest-api"></a>Управление прозрачным шифрованием данных с помощью REST API
 
Чтобы настроить TDE с помощью REST API, нужно подключиться в качестве владельца Azure, участника или диспетчера безопасности SQL. 

| Command | Description |
| --- | --- |
|[Создать или обновить сервер](/rest/api/sql/servers/createorupdate)|Добавляет удостоверение AAD в SQL Server (используется для предоставления доступа к Key Vault).|
|[Создать или обновить ключ сервера](/rest/api/sql/serverkeys/createorupdate)|Добавляет ключ Key Vault в SQL Server.|
|[Удалить ключ сервера](/rest/api/sql/serverkeys/delete)|Удаляет ключ Key Vault из SQL Server.|
|[Получить ключи сервера](/rest/api/sql/serverkeys/get)|Получает заданный ключ Key Vault из SQL Server.|
|[Список ключей серверов по серверам](/rest/api/sql/serverkeys/listbyserver)|Получает ключи Key Vault для SQL Server.|
|[Создать или обновить средство защиты шифрования](/rest/api/sql/encryptionprotectors/createorupdate)|Задает средство защиты TDE для SQL Server.|
|[Получить средство защиты шифрования](/rest/api/sql/encryptionprotectors/get)|Получает средство защиты TDE для SQL Server.|
|[Список средств защиты шифрования по серверам](/rest/api/sql/encryptionprotectors/listbyserver)|Получает средства защиты TDE для SQL Server.|
|[Создать или обновить конфигурацию прозрачного шифрования данных](/rest/api/sql/transparentdataencryptions/createorupdate)|Включает или отключает прозрачное шифрование данных для базы данных.|
|[Получить конфигурацию прозрачного шифрования данных](/rest/api/sql/transparentdataencryptions/get)|Получает конфигурацию прозрачного шифрования данных для базы данных.|
|[Список результатов конфигурации прозрачного шифрования данных](/rest/api/sql/transparentdataencryptionactivities/ListByConfiguration)|Получает результат шифрования для базы данных.|

## <a name="next-steps"></a>Следующие шаги

- Общее описание TDE см. в статье [Прозрачное шифрование данных (TDE)](transparent-data-encryption.md).

- Дополнительные сведения о TDE с поддержкой BYOK для базы данных и хранилища данных SQL Azure см. в статье [Прозрачное шифрование данных с поддержкой создания собственных ключей](transparent-data-encryption-byok-azure-sql.md).

- Инструкции по началу работы с TDE с поддержкой BYOK см. в руководстве [Включение прозрачного шифрования данных с использованием собственного ключа из хранилища ключей с помощью PowerShell](transparent-data-encryption-byok-azure-sql-configure.md).

- Дополнительные сведения о хранилище ключей см. на [странице документации по хранилищу ключей](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).
