---
title: Введение в пространство имен Microsoft.Data.SqlClient
description: Начальная страница для пространства имен Microsoft. Data. SqlClient.
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 4f4034c557c13054dcfb6ed425ca996b0c5363f6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452380"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Введение в пространство имен Microsoft.Data.SqlClient

![Download-DownArrow-Circled](../../ssdt/media/download.png)[Скачать ADO.NET](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

На этой странице описывается, как пространство имен Microsoft. Data. SqlClient предоставляет дополнительные функциональные возможности для существующего пространства имен System. Data. SqlClient.
  
## <a name="release-notes"></a>Заметки о выпуске
Все заметки о выпуске доступны в [репозитории GitHub](https://github.com/dotnet/SqlClient/tree/master/release-notes).

## <a name="new-features"></a>Новые возможности

### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>Новые возможности по сравнению с .NET Framework 4.7.2 System. Data. SqlClient

Классификация данных — доступна в базе данных SQL Azure и Microsoft SQL Server 2019 с CTP 2,0.

Поддержка UTF-8 — доступна в Microsoft SQL Server SQL Server 2019 с CTP 2,3.

### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>Новые возможности по сравнению с .NET Core 2,2 System. Data. SqlClient

Классификация данных — доступна в базе данных SQL Azure и Microsoft SQL Server 2019 с CTP 2,0.

Поддержка UTF-8 — доступна в Microsoft SQL Server SQL Server 2019 с CTP 2,3.

Always Encrypted с Енклавес-Always Encrypted доступен в Microsoft SQL Server 2016 и более поздних версиях. Поддержка анклава появилась в Microsoft SQL Server 2019 CTP 2,0.

Проверка подлинности — Active Directory режим проверки подлинности пароля.

### <a name="data-classification"></a>Классификация данных

Классификация данных предоставляет новый набор интерфейсов API, которые предоставляют доступ только для чтения и сведения о классификации объектов, полученных через SqlDataReader, когда базовый источник поддерживает эту функцию и содержит метаданные о [конфиденциальности данных и Классификация](../../relational-databases/security/sql-data-discovery-and-classification.md).

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

Поддержка UTF-8 не требует изменения кода приложения. Эти изменения SqlClient просто оптимизируют связь между клиентом и сервером, когда сервер поддерживает кодировку UTF-8, а базовые параметры сортировки столбца — UTF-8. Ознакомьтесь с разделом UTF-8 в разделе [новые возможности SQL Server 2019 предварительной версии](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Постоянное шифрование с помощью енклавес

В целом, существующая документация, использующая System. Data. SqlClient на .NET Framework **и встроенные поставщики хранилища главных ключей столбцов** , теперь должна работать и с .NET Core.

 [Разработка с использованием постоянного шифрования с поставщиком данных .NET Framework](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted: Защита конфиденциальных данных и хранение ключей шифрования в хранилище сертификатов Windows](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Проверка подлинности

Различные режимы проверки подлинности можно указать с помощью параметра строки подключения _проверки подлинности_ . Дополнительные сведения см. в [документации по склаусентикатионмесод](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Настраиваемые поставщики хранилища ключей, например поставщик Azure Key Vault, необходимо обновить для поддержки Microsoft. Data. SqlClient. Также для поддержки Microsoft. Data. SqlClient необходимо обновить поставщики анклава.
> Always Encrypted поддерживается только для целей .NET Framework и .NET Core. Она не поддерживается для .NET Standard, поскольку у .NET Standard отсутствуют определенные зависимости шифрования.
