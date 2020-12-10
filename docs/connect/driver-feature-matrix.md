---
title: Матрица поддержки функций драйверами
description: Узнайте, какие популярные функции поддерживаются в драйверах для SQL Server и где можно найти сведения о них.
ms.custom: ''
ms.date: 12/03/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-daenge
ms.openlocfilehash: 4fff9c04098bd0796f714d160864e4edb93613ac
ms.sourcegitcommit: 28fecbf61ae7b53405ca378e2f5f90badb1a296a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96595235"
---
# <a name="driver-feature-support-matrix-for-microsoft-sql-server"></a>Матрица поддержки функций драйверами для Microsoft SQL Server

Если вы планируете использовать функцию Microsoft SQL Server, она может быть доступна не во всех драйверах. Некоторые причины, по которым функции может не быть в конкретном драйвере:

- эта функция неприменима к технологии драйвера;
- эта функция является новой и еще не реализована для всех драйверов;
- эта функция не востребована в конкретном драйвере;
- в первую очередь реализуются другие функции.

Мы стремимся к тому, чтобы все драйверы поддерживали все функции, и прилагаем усилия, чтобы обеспечить одинаковый набор функций для всех драйверов. Однако это не всегда возможно. Чтобы выбрать подходящий для ваших нужд драйвер, ознакомьтесь со списком популярных функций и драйверов, которые их реализуют.

- [.NET](#table1)
- [ODBC](#table2);
- [OLE DB](#table2);
- [JDBC](#table2)
- [PHP](#table3)
- [Node.js и JavaScript](#table3)
- [Python](#table3)

| <a id="table1"></a>Функция | [Microsoft.<wbr>Data.<wbr>SqlClient (.NET Core)](ado-net/microsoft-ado-net-sql-server.md) | [Microsoft.<wbr>Data.<wbr>SqlClient (.NET Framework)](ado-net/microsoft-ado-net-sql-server.md) | System.<wbr>Data.<wbr>SqlClient (.NET Core) | [System.<wbr>Data.<wbr>SqlClient (.NET Framework)](/dotnet/framework/data/adonet/sql/) |
| :-- | :-- | :-- | :-- | :-- |
| [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) | [Да](ado-net/sql/sqlclient-support-always-encrypted.md) | [Да](ado-net/sql/sqlclient-support-always-encrypted.md) | | [Да](ado-net/sql/sqlclient-support-always-encrypted.md) |
| [Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md) | [Да](ado-net/sql/sqlclient-support-always-encrypted.md#enabling-always-encrypted-with-secure-enclaves) | [Да](ado-net/sql/sqlclient-support-always-encrypted.md#enabling-always-encrypted-with-secure-enclaves) | | [Да](ado-net/sql/sqlclient-support-always-encrypted.md#enabling-always-encrypted-with-secure-enclaves) |
| [Проверка подлинности Azure Active Directory с использованием маркера доступа](/azure/active-directory/develop/access-tokens) | [Да](/dotnet/api/system.data.sqlclient.sqlconnection.accesstoken) | [Да](/dotnet/api/microsoft.data.sqlclient.sqlconnection.accesstoken) | [Да](/dotnet/api/microsoft.data.sqlclient.sqlconnection.accesstoken) | [Да](/dotnet/api/microsoft.data.sqlclient.sqlconnection.accesstoken) |
| [Проверка подлинности Azure Active Directory с использованием пароля](/azure/sql-database/sql-database-aad-authentication) | [Да](ado-net/sql/azure-active-directory-authentication.md) | [Да](ado-net/sql/azure-active-directory-authentication.md) | | Да |
| [Интегрированная проверка подлинности Azure Active Directory](/azure/sql-database/sql-database-aad-authentication) | [Да](ado-net/sql/azure-active-directory-authentication.md) | [Да](ado-net/sql/azure-active-directory-authentication.md) | | Да |
| [Интерактивная проверка подлинности Azure Active Directory (MFA)](/azure/sql-database/sql-database-aad-authentication) | [Да](ado-net/sql/azure-active-directory-authentication.md) | [Да](ado-net/sql/azure-active-directory-authentication.md) | | Да |
| [Проверка подлинности Azure Active Directory с использованием управляемого удостоверения](/azure/active-directory/managed-identities-azure-resources/overview) | [Да](ado-net/sql/azure-active-directory-authentication.md) | [Да](ado-net/sql/azure-active-directory-authentication.md) | | |
| [Проверка подлинности Azure Active Directory субъекта-службы](/azure/active-directory/develop/app-objects-and-service-principals) | [Да](ado-net/sql/azure-active-directory-authentication.md) | [Да](ado-net/sql/azure-active-directory-authentication.md) | | |
| [Встроенная проверка подлинности Windows](/windows-server/security/windows-authentication/windows-authentication-overview) | [Да](ado-net/sql/authentication-sql-server.md) | [Да](ado-net/sql/authentication-sql-server.md) | [Да](/dotnet/framework/data/adonet/sql/authentication-in-sql-server) | [Да](/dotnet/framework/data/adonet/sql/authentication-in-sql-server) |
| [Массовое копирование](../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) | [Да](ado-net/sql/bulk-copy-operations-sql-server.md) | [Да](ado-net/sql/bulk-copy-operations-sql-server.md) | [Да](/dotnet/framework/data/adonet/sql/bulk-copy-operations-in-sql-server) | [Да](/dotnet/framework/data/adonet/sql/bulk-copy-operations-in-sql-server) |
| [Метаданные о конфиденциальности и классификации данных](../relational-databases/security/sql-data-discovery-and-classification.md) | [Да](ado-net/sql/data-classification.md) | [Да](ado-net/sql/data-classification.md) | Да | Да |
| [Режим MARS](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Да](ado-net/sql/multiple-active-result-sets-mars.md) | [Да](ado-net/sql/multiple-active-result-sets-mars.md) | [Да](/dotnet/framework/data/adonet/sql/multiple-active-result-sets-mars) | [Да](/dotnet/framework/data/adonet/sql/multiple-active-result-sets-mars) |
| [Типы пространственных данных](../relational-databases/spatial/spatial-data-sql-server.md) | | да | | Да |
| [Параметры, которые возвращают табличное значение (TVP)](../relational-databases/tables/use-table-valued-parameters-database-engine.md) | [Да](ado-net/sql/table-valued-parameters.md) | [Да](ado-net/sql/table-valued-parameters.md) | [Да](/dotnet/framework/data/adonet/sql/table-valued-parameters) | [Да](/dotnet/framework/data/adonet/sql/table-valued-parameters) |
| [MultiSubnetFailover](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](ado-net/sql/sqlclient-support-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](ado-net/sql/sqlclient-support-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](/dotnet/api/system.data.sqlclient.sqlconnectionstringbuilder.multisubnetfailover?view=netcore-1.0&preserve-view=true) | [Да](/dotnet/api/system.data.sqlclient.sqlconnectionstringbuilder.multisubnetfailover?view=netframework-4.8&preserve-view=true) |
| [Разрешение IP-адресов прозрачной сети](odbc/using-transparent-network-ip-resolution.md) | | [Да](/dotnet/api/microsoft.data.sqlclient.sqlconnection.connectionstring?view=sqlclient-dotnet-1.1&preserve-view=true) | | [Да](/dotnet/api/system.data.sqlclient.sqlconnection.connectionstring?view=netframework-4.8&preserve-view=true) |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

| <a id="table2"></a>Функция | [Драйвер ODBC для SQL Server в Windows](odbc/microsoft-odbc-driver-for-sql-server.md) | [Драйвер ODBC для SQL Server в Linux и macOS](odbc/microsoft-odbc-driver-for-sql-server.md) | [Драйвер JDBC для SQL Server](jdbc/microsoft-jdbc-driver-for-sql-server.md) | [Драйвер OLE DB для SQL Server](oledb/oledb-driver-for-sql-server.md) |
| :-- | :-- | :-- | :-- | :-- |
| [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) | [Да](odbc/using-always-encrypted-with-the-odbc-driver.md) | [Да](odbc/using-always-encrypted-with-the-odbc-driver.md) | [Да](jdbc/using-always-encrypted-with-the-jdbc-driver.md) |
| [Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md) | [Да](odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves) | [Да](odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves) | [Да](jdbc/using-always-encrypted-with-the-jdbc-driver.md) | |
| [Проверка подлинности Azure Active Directory с использованием маркера доступа](/azure/active-directory/develop/access-tokens) | [Да](odbc/using-azure-active-directory.md#authenticating-with-an-access-token) | [Да](odbc/using-azure-active-directory.md#authenticating-with-an-access-token) | [Да](jdbc/connecting-using-azure-active-directory-authentication.md#connecting-using-access-token) | [Да](oledb/features/using-azure-active-directory.md) |
| [Проверка подлинности Azure Active Directory с использованием пароля](/azure/sql-database/sql-database-aad-authentication) |  [Да](odbc/using-azure-active-directory.md) | [Да](odbc/using-azure-active-directory.md) | [Да](jdbc/connecting-using-azure-active-directory-authentication.md) | [Да](oledb/features/using-azure-active-directory.md) |
| [Интегрированная проверка подлинности Azure Active Directory](/azure/sql-database/sql-database-aad-authentication) | [Да](odbc/using-azure-active-directory.md) | [Да](odbc/using-azure-active-directory.md) | [Да](jdbc/connecting-using-azure-active-directory-authentication.md) | [Да](oledb/features/using-azure-active-directory.md) |
| [Интерактивная проверка подлинности Azure Active Directory (MFA)](/azure/sql-database/sql-database-aad-authentication) | [Да](odbc/using-azure-active-directory.md) | | | [Да](oledb/features/using-azure-active-directory.md) |
| [Проверка подлинности Azure Active Directory с использованием управляемого удостоверения](/azure/active-directory/managed-identities-azure-resources/overview) | [Да](odbc/using-azure-active-directory.md) | [Да](odbc/using-azure-active-directory.md) | [Да](jdbc/connecting-using-azure-active-directory-authentication.md) | [Да](oledb/features/using-azure-active-directory.md) |
| [Проверка подлинности Azure Active Directory субъекта-службы](/azure/active-directory/develop/app-objects-and-service-principals) | | | | [Да](oledb/features/using-azure-active-directory.md) |
| [Встроенная проверка подлинности Windows](/windows-server/security/windows-authentication/windows-authentication-overview) | Да | [Да](odbc/linux-mac/using-integrated-authentication.md) | [Да](jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) | Да |
| [Массовое копирование](../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) | [Да](../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md) | [Да](../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md) | [Да](jdbc/using-bulk-copy-with-the-jdbc-driver.md) | [Да](oledb/features/performing-bulk-copy-operations.md) |
| [Метаданные обнаружения и классификации данных](../relational-databases/security/sql-data-discovery-and-classification.md) | [Да](odbc/data-classification.md) | [Да](odbc/data-classification.md) | [Да](jdbc/data-discovery-classification-sample.md) | |
| [Режим MARS](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Да](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Да](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | | [Да](oledb/features/using-multiple-active-result-sets-mars.md) |
| [Типы пространственных данных](../relational-databases/spatial/spatial-data-sql-server.md) | | | [Да](jdbc/use-spatial-datatypes.md) | |
| [Параметры, которые возвращают табличное значение (TVP)](../relational-databases/tables/use-table-valued-parameters-database-engine.md) | [Да](../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md) | [Да](../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md) | [Да](jdbc/using-table-valued-parameters.md) | [Да](oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) |
| [MultiSubnetFailover](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) | [Да](oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) |
| [Разрешение IP-адресов прозрачной сети](odbc/using-transparent-network-ip-resolution.md) | [Да](odbc/using-transparent-network-ip-resolution.md) | [Да](odbc/using-transparent-network-ip-resolution.md) | [Да](jdbc/setting-the-connection-properties.md) | [Да](oledb/features/using-transparent-network-ip-resolution.md) |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

| <a id="table3"></a>Функция | [Драйверы PHP для SQL Server в Windows](php/microsoft-php-driver-for-sql-server.md)<sup>[1](#note1)</sup> | [Драйверы PHP для SQL Server в Linux и macOS](php/microsoft-php-driver-for-sql-server.md)<sup>[1](#note1)</sup> | [Tedious (Node.js)](node-js/node-js-driver-for-sql-server.md) | [pyODBC (Python)](python/pyodbc/python-sql-driver-pyodbc.md)<sup>[1](#note1)</sup> |
| :-- | :-- | :-- | :-- | :-- |
| [Always Encrypted](../relational-databases/security/encryption/always-encrypted-database-engine.md) | [Да](php/using-always-encrypted-php-drivers.md) | [Да](php/using-always-encrypted-php-drivers.md) | | Да |
| [Always Encrypted с безопасными анклавами](../relational-databases/security/encryption/always-encrypted-enclaves.md) | [Да](php/always-encrypted-secure-enclaves.md) | [Да](php/always-encrypted-secure-enclaves.md) | | Да |
| [Проверка подлинности Azure Active Directory с использованием маркера доступа](/azure/active-directory/develop/access-tokens) | [Да](php/azure-active-directory.md) | [Да](php/azure-active-directory.md) | [Да](https://tediousjs.github.io/tedious/api-connection.html#function_newConnection) | Да |
| [Проверка подлинности Azure Active Directory с использованием пароля](/azure/sql-database/sql-database-aad-authentication) | [Да](php/azure-active-directory.md) | [Да](php/azure-active-directory.md) | [Да](https://tediousjs.github.io/tedious/api-connection.html#function_newConnection) | Да |
| [Интегрированная проверка подлинности Azure Active Directory](/azure/sql-database/sql-database-aad-authentication) | [Да](php/azure-active-directory.md) | [Да](php/azure-active-directory.md) | | Да |
| [Интерактивная проверка подлинности Azure Active Directory (MFA)](/azure/sql-database/sql-database-aad-authentication) | | | | Да<sup>[2](#note2)</sup> |
| [Проверка подлинности Azure Active Directory с использованием управляемого удостоверения](/azure/active-directory/managed-identities-azure-resources/overview) | [Да](php/azure-active-directory.md) | [Да](php/azure-active-directory.md) | [Да](https://tediousjs.github.io/tedious/api-connection.html#function_newConnection) | Да |
| [Проверка подлинности Azure Active Directory субъекта-службы](/azure/active-directory/develop/app-objects-and-service-principals) | | | | |
| [Встроенная проверка подлинности Windows](/windows-server/security/windows-authentication/windows-authentication-overview) | [Да](php/how-to-connect-using-windows-authentication.md) | [Да](odbc/linux-mac/using-integrated-authentication.md) | | Да |
| [Массовое копирование](../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) | | | [Да](https://tediousjs.github.io/tedious/bulk-load.html) | |
| [Метаданные обнаружения и классификации данных](../relational-databases/security/sql-data-discovery-and-classification.md) | да | Да | | |
| [Режим MARS](../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md) | [Да](php/how-to-disable-multiple-active-resultsets-mars.md) | [Да](php/how-to-disable-multiple-active-resultsets-mars.md) | | Да |
| [Типы пространственных данных](../relational-databases/spatial/spatial-data-sql-server.md) | | | | |
| [Параметры, которые возвращают табличное значение (TVP)](../relational-databases/tables/use-table-valued-parameters-database-engine.md) | | | [Да](https://tediousjs.github.io/tedious/parameters.html) | Да |
| [MultiSubnetFailover](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) | [Да](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | [Да](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | | [Да](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md#connecting-with-multisubnetfailover) |
| [Разрешение IP-адресов прозрачной сети](odbc/using-transparent-network-ip-resolution.md) | [Да](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | [Да](php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) | | [Да](odbc/using-transparent-network-ip-resolution.md) |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<a id="note1"></a><sup>1</sup> Поскольку эти драйверы зависят от Microsoft ODBC Driver for SQL Server, необходимо также использовать версию драйвера, поддерживающую эту функцию.

<a id="note2"></a><sup>2</sup> Только в Windows.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
