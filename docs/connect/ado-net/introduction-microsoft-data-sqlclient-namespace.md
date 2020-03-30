---
title: Введение в пространство имен Microsoft.Data.SqlClient
description: Вводная страница для пространства имен Microsoft.Data.SqlClient.
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: dbc76f1a2ee93faf642d923d3a543eee40d5348b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897117"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Введение в пространство имен Microsoft.Data.SqlClient

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Заметки о выпуске для Microsoft.Data.SqlClient 1.1.0

Заметки о выпуске также доступны в репозитории GitHub: [Заметки о выпуске 1.1](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

### <a name="new-features"></a>Новые возможности

#### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами.

Always Encrypted доступна начиная с Microsoft SQL Server 2016. Безопасные анклавы доступны начиная с Microsoft SQL Server 2019. Чтобы использовать функцию анклава, строки подключения должны включать необходимый протокол и URL-адрес аттестации. Примеры:

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

Дополнительные сведения см. в статье

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

Классификация данных предоставляет новый набор API-интерфейсов, которые предоставляют сведения только для чтения о конфиденциальности и классификации данных для объектов, полученных через SqlDataReader, если базовый источник поддерживает эту функцию и содержит метаданные о [конфиденциальности и классификации данных](../../relational-databases/security/sql-data-discovery-and-classification.md).

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

Поддержка UTF-8 не требует изменения кода приложения. Эти изменения SqlClient просто оптимизируют связь между клиентом и сервером, когда сервер поддерживает UTF-8, а базовым параметром сортировки столбца является UTF-8. См. раздел о UTF-8 в статье [Новые возможности SQL Server 2019 (15.x)](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Always encrypted с безопасными анклавами

В целом, существующая документация, использующая System.Data.SqlClient на .NET Framework **и встроенные поставщики хранилища главных ключей столбцов**, теперь должны также работать с .NET Core.

 [Разработка с использованием постоянного шифрования с поставщиком данных .NET Framework](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted: защита конфиденциальных данных и хранение ключей шифрования в хранилище сертификатов Windows](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Аутентификация

С помощью параметра строки подключения _Аутентификация_ можно указать различные режимы проверки подлинности. Дополнительные сведения см. в [документации по SqlAuthenticationMethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Настраиваемые поставщики хранилища ключей, например поставщик Azure Key Vault, необходимо обновить, чтобы они поддерживали Microsoft.Data.SqlClient. Также для поддержки Microsoft.Data.SqlClient необходимо обновить поставщики анклава.
> Always Encrypted поддерживается только для целевых объектов .NET Framework и .NET Core. Функция не поддерживается для .NET Standard, поскольку в .NET Standard отсутствуют определенные зависимости шифрования.
