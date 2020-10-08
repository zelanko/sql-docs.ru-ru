---
title: Введение в пространство имен Microsoft.Data.SqlClient
description: Узнайте подробнее о пространстве имен Microsoft.Data.SqlClient и о том, почему это предпочтительный способ подключения к SQL для приложений .NET.
ms.date: 09/29/2020
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: d72beeaf5b7652e040dd5bbe5f20373e655f822a
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725705"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Введение в пространство имен Microsoft.Data.SqlClient

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-20"></a>Заметки о выпуске для Microsoft.Data.SqlClient 2.0

Заметки о выпуске также доступны в репозитории GitHub: [Заметки о выпуске 2.0](https://github.com/dotnet/SqlClient/tree/master/release-notes/2.0).

### <a name="breaking-changes"></a>Критические изменения

- Модификатор доступа для интерфейса поставщика анклава `SqlColumnEncryptionEnclaveProvider` изменен с `public` на `internal`.

- Константы в классе `SqlClientMetaDataCollectionNames` были обновлены, чтобы отражать изменения в SQL Server.

- Теперь драйвер будет выполнять проверку сертификата сервера, когда целевой SQL Server применяет TLS-шифрование, которое используется по умолчанию для подключений Azure.

- `SqlDataReader.GetSchemaTable()` теперь возвращает пустой `DataTable` вместо `null`.

- Теперь драйвер выполняет округление по десятичной шкале, что соответствует поведению SQL Server. Для обеспечения обратной совместимости с помощью параметра AppContext можно включить предыдущее поведение, когда выполнялось усечение.

- Для приложений .NET Framework, использующих **Microsoft.Data.SqlClient**, файлы SNI.dll, ранее загруженные в папки `bin\x64` и `bin\x86`, теперь называются `Microsoft.Data.SqlClient.SNI.x64.dll` и ` Microsoft.Data.SqlClient.SNI.x86.dll` и будут загружены в каталог `bin`.

- Новые синонимы свойств строки подключения заменят старые свойства при получении строки подключения из `SqlConnectionStringBuilder` для обеспечения согласованности. [Подробнее](#new-connection-string-property-synonyms)

### <a name="new-features"></a>новые функции;

#### <a name="dns-failure-resiliency"></a>Устойчивость к сбоям DNS

Теперь драйвер будет кэшировать IP-адреса всех успешных подключений к конечной точке SQL Server, которая поддерживает эту функцию. Если во время попытки подключения происходит сбой разрешения DNS, драйвер пытается установить подключение с помощью кэшированного IP-адреса для этого сервера, если таковой существует. 

#### <a name="eventsource-tracing"></a>Трассировка EventSource

В этом выпуске реализована поддержка записи журналов трассировки событий для отладки приложений. Чтобы записать эти события, клиентские приложения должны ожидать передачи данных о событиях от реализации EventSource для SqlClient.

```
Microsoft.Data.SqlClient.EventSource
```

Дополнительные сведения см. в разделе [Включение трассировки событий в SqlClient](enable-eventsource-tracing.md).

#### <a name="enabling-managed-networking-on-windows"></a>Включение управляемых сетей в Windows

Новый параметр AppContext **Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows** позволяет использовать управляемую реализацию SNI в Windows для тестирования и отладки. Этот параметр позволяет переключить поведение драйвера на использование управляемого SNI в проектах .NET Core 2.1+ и .NET Standard 2.0+ в Windows, устраняя все зависимости от собственных библиотек для библиотеки Microsoft.Data.SqlClient.

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows", true);
```

Полный список доступных параметров в драйвере см. в разделе [Параметры AppContext в SqlClient](appcontext-switches.md).

#### <a name="enabling-decimal-truncation-behavior"></a>Включение усечения десятичных чисел 

Драйвер будет по умолчанию округлять десятичные числа, как это делается SQL Server. Для обеспечения обратной совместимости можно задать для параметра AppContext **Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal** значение **true**.

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal", true);
```

#### <a name="new-connection-string-property-synonyms"></a>Новые синонимы свойств строки подключения

Для следующих свойств строки подключения были добавлены новые синонимы, чтобы избежать путаницы в свойствах, состоящих более чем из одного слова. Старые имена свойств будут по-прежнему поддерживаться для обратной совместимости, но при получении строки подключения из [SqlConnectionStringBuilder](/dotnet/api/microsoft.data.sqlclient.sqlconnectionstringbuilder) будут включаться новые свойства строки подключения.

|Существующее свойство строки подключения|Новый синоним|
|-----------------------------------|-----------|
| ApplicationIntent | Назначение приложения |
| ConnectRetryCount | Connect Retry Count |
| ConnectRetryInterval | Connect Retry Interval |
| PoolBlockingPeriod | Pool Blocking Period |
| MultipleActiveResultSets | Multiple Active Result Sets |
| MultiSubnetFailover | Multiple Subnet Failover |
| TransparentNetworkIPResolution | Transparent Network IP Resolution |
| TrustServerCertificate | Надежный сертификат сервера |

#### <a name="sqlbulkcopy-rowscopied-property"></a>Свойство SqlBulkCopy RowsCopied

Свойство RowsCopied предоставляет доступ только для чтения к количеству строк, которые были обработаны в текущей операции с массовым копированием. Это значение не обязательно должно быть равно конечному количеству строк, добавляемых в целевую таблицу. 

#### <a name="connection-open-overrides"></a>Переопределение открытия соединения

Поведение по умолчанию для SqlConnection.Open() можно переопределить, чтобы отключить 10-секундную задержку и автоматические попытки подключения, активируемые временными ошибками.

```csharp
using SqlConnection sqlConnection = new SqlConnection("Data Source=(local);Integrated Security=true;Initial Catalog=AdventureWorks;");
sqlConnection.Open(SqlConnectionOverrides.OpenWithoutRetry);
```

> [!NOTE]
> Обратите внимание, что это переопределение можно применить только к SqlConnection.Open(), а не к SqlConnection.OpenAsync().

#### <a name="username-support-for-active-directory-interactive-mode"></a>Поддержка имени пользователя для интерактивного режима Active Directory

Имя пользователя может быть указано в строке подключения при использовании режима интерактивной проверки подлинности Azure Active Directory для .NET Framework и .NET Core.

Задайте имя пользователя, используя **идентификатор пользователя** или свойство строки подключения **UID**.

```
"Server=<server name>; Database=<db name>; Authentication=Active Directory Interactive; User Id=<username>;"
```

#### <a name="order-hints-for-sqlbulkcopy"></a>Указания порядка для SqlBulkCopy

Для повышения производительности операций массового копирования в таблицах с кластеризованными индексами можно предоставить указания порядка. Дополнительные сведения см. в разделе об [операциях массового копирования](sql/bulk-copy-order-hints.md).

#### <a name="sni-dependency-changes"></a>Изменения зависимостей SNI

Microsoft.Data.SqlClient (.NET Core и .NET Standard) в Windows теперь зависят от **Microsoft.Data.SqlClient.SNI.runtime** вместо **runtime.native.System.Data.SqlClient.SNI**. Новая зависимость добавляет поддержку платформы ARM в дополнение к поддерживаемым платформам ARM64, x64 и x86 в Windows.

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Заметки о выпуске для Microsoft.Data.SqlClient 1.1.0

Заметки о выпуске также доступны в репозитории GitHub: [Заметки о выпуске 1.1](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

### <a name="new-features"></a>новые функции;

#### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами.

Always Encrypted доступна начиная с Microsoft SQL Server 2016. Безопасные анклавы доступны начиная с Microsoft SQL Server 2019. Чтобы использовать функцию анклава, строки подключения должны включать необходимый протокол и URL-адрес аттестации. Пример:

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

Дополнительные сведения см. в разделе:

- [Поддержка SqlClient для Always Encrypted](sql/sqlclient-support-always-encrypted.md)
- [Руководство. Разработка приложения .NET с помощью Always Encrypted с безопасными анклавами](sql/tutorial-always-encrypted-enclaves-develop-net-apps.md)

## <a name="release-notes-for-microsoftdatasqlclient-10"></a>Заметки о выпуске для Microsoft.Data.SqlClient 1.0

Первоначальный выпуск пространства имен Microsoft.Data.SqlClient предоставляет дополнительные функциональные возможности для существующего пространства имен System.Data.SqlClient.
Заметки о выпуске также доступны в репозитории GitHub: [Заметки о выпуске 1.0](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.0).

### <a name="new-features"></a>новые функции;

#### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>Новые возможности по сравнению с .NET Framework 4.7.2 System.Data.SqlClient

- **Классификация данных**. Доступна в Базе данных SQL Azure и Microsoft SQL Server 2019.

- **Поддержка UTF-8**. Доступна в Microsoft SQL Server 2019.

#### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>Новые возможности по сравнению с .NET Core 2.2 System.Data.SqlClient

- **Классификация данных**. Доступна в Базе данных SQL Azure и Microsoft SQL Server 2019.

- **Поддержка UTF-8**. Доступна в Microsoft SQL Server 2019.

- **Проверки подлинности**. Режим проверки подлинности с помощью пароля AD DS.

### <a name="data-classification"></a>Классификация данных

Классификация данных предоставляет новый набор API-интерфейсов, которые предоставляют сведения только для чтения о конфиденциальности и классификации данных для объектов, полученных через SqlDataReader, если базовый источник поддерживает эту функцию и содержит метаданные о [конфиденциальности и классификации данных](../../relational-databases/security/sql-data-discovery-and-classification.md). См. пример приложения в разделе [Обнаружение и классификация данных в SqlClient](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

```csharp
public class SqlDataReader
{
    public Microsoft.Data.SqlClient.DataClassification.SensitivityClassification SensitivityClassification
}

namespace Microsoft.Data.SqlClient.DataClassification
{
    public class ColumnSensitivity
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.SensitivityProperty> SensitivityProperties
    }
    public class InformationType
    {
        public string Id
        public string Name
    }
    public class Label
    {
        public string Id
        public string Name
    }
    public class SensitivityClassification
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.ColumnSensitivity> ColumnSensitivities
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.InformationType> InformationTypes
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.Label> Labels
    }
    public class SensitivityProperty
    {
        public Microsoft.Data.SqlClient.DataClassification.InformationType InformationType
        public Microsoft.Data.SqlClient.DataClassification.Label Label
    }
}
```

### <a name="utf-8-support"></a>Поддержка UTF-8.

Поддержка UTF-8 не требует изменения кода приложения. Эти изменения SqlClient оптимизируют связь между клиентом и сервером, когда сервер поддерживает UTF-8, а базовым параметром сортировки столбца является UTF-8. См. раздел о UTF-8 в статье [Новые возможности SQL Server 2019](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Always encrypted с безопасными анклавами

В целом, существующая документация, использующая System.Data.SqlClient на .NET Framework **и встроенные поставщики хранилища главных ключей столбцов**, теперь должны также работать с .NET Core.

 [Разработка с использованием постоянного шифрования с поставщиком данных .NET Framework](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted: защита конфиденциальных данных и хранение ключей шифрования в хранилище сертификатов Windows](/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Аутентификация

С помощью параметра строки подключения _Аутентификация_ можно указать различные режимы проверки подлинности. Дополнительные сведения см. в [документации по SqlAuthenticationMethod](/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Настраиваемые поставщики хранилища ключей, например поставщик Azure Key Vault, необходимо обновить, чтобы они поддерживали Microsoft.Data.SqlClient. Также для поддержки Microsoft.Data.SqlClient необходимо обновить поставщики анклава.
> Always Encrypted поддерживается только для целевых объектов .NET Framework и .NET Core. Функция не поддерживается для .NET Standard, поскольку в .NET Standard отсутствуют определенные зависимости шифрования.