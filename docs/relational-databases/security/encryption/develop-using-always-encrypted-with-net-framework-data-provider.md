---
title: Always Encrypted с поставщиком данных .NET Framework
description: Узнайте, как разрабатывать приложения .NET с помощью функции Always Encrypted для SQL Server.
ms.custom: seo-lt-2019
ms.date: 10/31/2019
ms.prod: sql
ms.prod_service: security, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 827e509e-3c4f-4820-aa37-cebf0f7bbf80
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c442568ad7764ba0f9031a02a8080499555d26f
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79286988"
---
# <a name="using-always-encrypted-with-the-net-framework-data-provider-for-sql-server"></a>Using Always Encrypted with the .NET Framework Data Provider for SQL Server (Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В этой статье содержатся сведения о разработке приложений .NET с помощью [Always Encrypted](always-encrypted-database-engine.md) или [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) и [Поставщика данных .NET Framework для SQL Server](https://msdn.microsoft.com/library/kb9s9ks0(v=vs.110).aspx).

Функция Always Encrypted позволяет шифровать конфиденциальные данные в клиентских приложениях, не раскрывая данные или ключи шифрования для SQL Server или Базы данных SQL Azure. Драйвер с поддержкой постоянного шифрования, такой как поставщик данных .NET Framework для SQL Server, реализует это за счет прозрачного шифрования и расшифровки конфиденциальных данных в клиентском приложении SQL Server. Драйвер автоматически определяет, какие параметры запроса соответствуют важным столбцам базы данных (защищенным с помощью Always Encrypted), и шифрует значения этих параметров перед передачей данных в SQL Server или Базу данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. в разделе [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md) и [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md).

## <a name="prerequisites"></a>Предварительные требования

- Настройте функцию постоянного шифрования в базе данных. В процесс настройки входят действия по подготовке ключей постоянного шифрования и настройке шифрования для выбранных столбцов базы данных. Если в базе данных Always Encrypted еще не настроен, следуйте инструкциям в разделе [Начало работы с Always Encrypted](always-encrypted-database-engine.md#getting-started-with-always-encrypted).
- Убедитесь, что на компьютере, предназначенном для разработки, установлена платформа .NET Framework 4.6.1 или более поздней версии. Дополнительные сведения см. в разделе [.NET Framework 4.6](https://msdn.microsoft.com/library/w0x726c2(v=vs.110).aspx). Также необходимо убедиться, что в среде разработки в качестве целевой версии платформы установлена платформа .NET Framework 4.6 или более поздней версии. Если вы используете Visual Studio, обратитесь к разделу [Руководство. Определение целевой версии платформы .NET Framework](https://msdn.microsoft.com/library/bb398202.aspx). 

> [!NOTE]
> Уровень поддержки постоянного шифрования зависит от конкретной версии платформы .NET Framework. Дополнительные сведения см. в разделе справки по API постоянного шифрования ниже.

## <a name="enabling-always-encrypted-for-application-queries"></a>Включение Always Encrypted для запросов приложений
Самым простым способом включения шифрования параметров и расшифровки результатов запросов к зашифрованным столбцам является установка для ключевого слова строки подключения "Параметр шифрования столбца" значения **Включено**.

Ниже приведен пример строки подключения, включающий постоянное шифрование.

```cs
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true; Column Encryption Setting=enabled";
SqlConnection connection = new SqlConnection(connectionString);
```

Далее приведен эквивалент примера с использованием свойства SqlConnectionStringBuilder.ColumnEncryptionSetting.

```cs
SqlConnectionStringBuilder strbldr = new SqlConnectionStringBuilder();
strbldr.DataSource = "server63";
strbldr.InitialCatalog = "Clinic";
strbldr.IntegratedSecurity = true;
strbldr.ColumnEncryptionSetting = SqlConnectionColumnEncryptionSetting.Enabled;
SqlConnection connection = new SqlConnection(strbldr.ConnectionString);
```

Постоянное шифрование также можно включить для отдельных запросов. См. раздел **Управление влиянием постоянного шифрования на производительность** ниже.
Включения функции Always Encrypted недостаточно для успешного шифрования или расшифровки. Необходимо также проверить выполнение следующих условий:
- Приложение имеет разрешения *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* для базы данных, необходимые для доступа к метаданным о ключах постоянного шифрования в базе данных. Для дополнительных сведений см. страницу [о разрешениях в статье "Always Encrypted (ядро СУБД)"](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7).
- Приложение может получить доступ к главному ключу столбца, который защищает ключи шифрования столбцов, шифрующие запрашиваемые столбцы базы данных.

## <a name="enabling-always-encrypted-with-secure-enclaves"></a>Включение Always Encrypted с безопасными анклавами

Начиная с версии .NET Framework 4.7.2 драйвер поддерживает [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md). 

Чтобы включить использование анклава при подключении к [!INCLUDE [sssqlv15-md](../../../includes/sssqlv15-md.md)] или более поздней версии, необходимо настроить приложение и поставщик данных .NET Framework для SQL Server, чтобы включить вычисления анклава и аттестацию анклава. 

Общие сведения о роли клиентского драйвера в вычислениях анклава и аттестации анклава см. в статье [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md). 

Настройка приложения:

1. Интегрируйте пакет NuGet [Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders) в приложение. NuGet — это библиотека поставщиков анклавов, которая реализует логику на стороне клиента для протокола аттестации, а также для установки безопасного канала с безопасным анклавом внутри SQL Server.  
2. Обновите конфигурацию приложения (например, в файле web.config или app.config), чтобы определить сопоставление для типа анклава, с которым был настроен ваш экземпляр [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] (см. раздел [Настройка типа анклава для параметра конфигурации сервера Always Encrypted](../../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)). [!INCLUDE [sssqlv15-md](../../../includes/sssqlv15-md.md)] поддерживает анклавы VBS и службу защитника узлов для аттестации. Поэтому необходимо соотнести тип анклава VBS с классом Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider из пакета NuGet. 
3. Включите вычисления анклава для подключения из приложения к базе данных, задав ключевое слово URL-адреса аттестации анклава в строке подключения к конечной точке аттестации. В качестве значения ключевого слова следует задать конечную точку аттестации сервера HGS, настроенную в вашей среде. 

Пошаговое руководство см. в статье [Учебник. Разработка приложения .NET Framework с помощью Always Encrypted с безопасными анклавами](../tutorial-always-encrypted-enclaves-develop-net-framework-apps.md)

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Получение и изменение данных в зашифрованных столбцах

После включения постоянного шифрования для запросов приложений можно использовать стандартные API-интерфейсы для ADO.NET (см. раздел [Получение и изменение данных в ADO.NET](https://msdn.microsoft.com/library/ms254937(v=vs.110).aspx)) или API-интерфейсы [поставщика данных .NET Framework для SQL Server](https://msdn.microsoft.com/library/kb9s9ks0(v=vs.110).aspx) , определенные в [пространстве имен System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx), чтобы получать или изменять данные в зашифрованных столбцах базы данных. Если приложение имеет необходимые разрешения для базы данных и может обращаться к главному ключу столбца, поставщик данных .NET Framework для SQL Server будет шифровать все параметры запроса, предназначенные для зашифрованных столбцов, и расшифровывать данные, извлекаемые из зашифрованных столбцов с возвращаемыми значениями типов .NET в виде открытого текста, которые соответствуют типам данным SQL Server, заданным для столбцов в схеме базы данных.
Если функция Always Encrypted не включена, выполнение запросов с параметрами, предназначенными для зашифрованных столбцов, завершится ошибкой. Запросы по-прежнему могут получать данные из зашифрованных столбцов, пока для них не будут указаны параметры, предназначенные для зашифрованных столбцов. Однако поставщик данных .NET Framework для SQL Server не будет пытаться расшифровать все значения, полученные из зашифрованных столбцов, и приложение будет получать двоичные зашифрованные данные (в виде массивов байтов).

В приведенной ниже таблице описывается поведение запросов в зависимости от того, включено постоянное шифрование или нет.

|Характеристика запроса | Постоянное шифрование включено, и приложение может получать доступ к ключам и метаданным ключей|Функция Always Encrypted включена, и приложение не может получать доступ к ключам и метаданным ключей | Постоянное шифрование отключено|
|:---|:---|:---|:---|
| Запросы с параметрами, предназначенными для зашифрованных столбцов. | Значения параметров прозрачно шифруются. | Error | Error|
| Запросы, получающие данные из зашифрованных столбцов, без параметров, предназначенных для зашифрованных столбцов.| Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает значения типов данных .NET в виде открытого текста, которые соответствуют типам SQL Server, настроенным для зашифрованных столбцов. | Error | Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде массивов байтов (byte[]). 

В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В примерах предполагается использование целевой таблицы с приведенной ниже схемой. Столбцы SSN и BirthDate зашифрованы.


```sql
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1), 
 [SSN] [char](11) COLLATE Latin1_General_BIN2 
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL, 
 [BirthDate] [date] 
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="inserting-data-example"></a>Пример вставки данных

В этом примере показана вставка строки в таблицу Patients. Следует отметить следующее.
- В образце кода нет ничего, связанного с шифрованием. Поставщик данных .NET Framework для SQL Server автоматически обнаруживает и шифрует параметры *paramSSN* и *paramBirthdate* , предназначенные для зашифрованных столбцов. В этом случае шифрование является прозрачным для приложения. 
- Значения, вставляемые в столбцы базы данных, включая зашифрованные столбцы, передаются как объекты [SqlParameter](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.aspx) . Несмотря на то, что при отправке значений в незашифрованные столбцы использовать параметр **SqlParameter** необязательно (но настоятельно рекомендуется, так как он помогает предотвратить внедрение кода SQL), он требуется для значений, предназначенных для зашифрованных столбцов. Если значения, вставленные в столбцы SSN или BirthDate, были переданы в качестве литералов, внедренных в инструкцию запроса, выполнение запроса завершится ошибкой, так как поставщик данных .NET Framework для SQL Server не сможет определить значения в зашифрованных столбцах и поэтому не сможет зашифровать значения. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
- Для типа данных параметра, предназначенного для столбца SSN, задана строка ANSI (отличная от Юникода), которая сопоставляется с типом данных char и varchar SQL Server. Если для типа параметра была задана строка в Юникоде (String), которая сопоставляется с типом данных char и varchar, выполнение запроса завершится ошибкой, так как постоянное шифрование не поддерживает преобразования из зашифрованных значений nchar и nvarchar в зашифрованные значения char и varchar. Сведения о сопоставлении типов данных см. в разделе [Сопоставления типов данных SQL Server](/dotnet/framework/data/adonet/sql-server-data-type-mappings) .
- В качестве типа данных параметра, вставляемого в столбец BirthDate, явным образом задан целевой тип данных SQL Server. Для этого использовалось свойство [SqlParameter.SqlDbType Property](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sqldbtype.aspx), а не неявное сопоставление типов .NET с типами данных SQL Server, применяемыми при работе со свойством [SqlParameter.DbType Property](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.dbtype.aspx). По умолчанию [структура DateTime](https://msdn.microsoft.com/library/system.datetime.aspx) сопоставляется с типом данных datetime SQL Server. Так как типом данных столбца BirthDate является date и постоянное шифрование не поддерживает преобразование зашифрованных значений datetime в зашифрованные значения date, использование сопоставления по умолчанию приведет к ошибке. 

```cs
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true; Column Encryption Setting=enabled";
using (SqlConnection connection = new SqlConnection(strbldr.ConnectionString))
{
   using (SqlCommand cmd = connection.CreateCommand())
   {
      cmd.CommandText = @"INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (@SSN, @FirstName, @LastName, @BirthDate);";

      SqlParameter paramSSN = cmd.CreateParameter();
      paramSSN.ParameterName = @"@SSN";
      paramSSN.DbType = DbType.AnsiStringFixedLength;
      paramSSN.Direction = ParameterDirection.Input;
      paramSSN.Value = "795-73-9838";
      paramSSN.Size = 11;
      cmd.Parameters.Add(paramSSN);

      SqlParameter paramFirstName = cmd.CreateParameter();
      paramFirstName.ParameterName = @"@FirstName";
      paramFirstName.DbType = DbType.String;
      paramFirstName.Direction = ParameterDirection.Input;
      paramFirstName.Value = "Catherine";
      paramFirstName.Size = 50;
      cmd.Parameters.Add(paramFirstName);

      SqlParameter paramLastName = cmd.CreateParameter();
      paramLastName.ParameterName = @"@LastName";
      paramLastName.DbType = DbType.String;
      paramLastName.Direction = ParameterDirection.Input;
      paramLastName.Value = "Abel";
      paramLastName.Size = 50;
      cmd.Parameters.Add(paramLastName);

      SqlParameter paramBirthdate = cmd.CreateParameter();
      paramBirthdate.ParameterName = @"@BirthDate";
      paramBirthdate.SqlDbType = SqlDbType.Date;
      paramBirthdate.Direction = ParameterDirection.Input;
      paramBirthdate.Value = new DateTime(1996, 09, 10);
      cmd.Parameters.Add(paramBirthdate);

      cmd.ExecuteNonQuery();
   } 
}
```

### <a name="retrieving-plaintext-data-example"></a>Пример получения данных в виде открытого текста

В следующем примере показана фильтрация данных на основе зашифрованных значений и получение данных в виде открытого текста из зашифрованных столбцов. Следует отметить следующее.
- Значение, используемое в предложении WHERE для фильтрации по столбцу SSN, необходимо передать с помощью SqlParameter, чтобы поставщик данных .NET Framework для SQL Server мог его прозрачно зашифровать перед отправкой в базу данных.
- Все значения, выводимые программой, будут представлены в виде обычного текста, так как поставщик данных .NET Framework для SQL Server прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.


> [!NOTE]
> Запросы могут выполнять сравнение на равенство для столбцов, если они шифруются с помощью детерминированного шифрования. Дополнительные сведения см. в разделе [Выбор детерминированного или случайного шифрования](always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```cs
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true; Column Encryption Setting=enabled";
    
using (SqlConnection connection = new SqlConnection(strbldr.ConnectionString))
 {
    using (SqlCommand cmd = connection.CreateCommand())
 {

 cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN=@SSN";
 SqlParameter paramSSN = cmd.CreateParameter();
 paramSSN.ParameterName = @"@SSN";
 paramSSN.DbType = DbType.AnsiStringFixedLength;
 paramSSN.Direction = ParameterDirection.Input;
 paramSSN.Value = "795-73-9838";
 paramSSN.Size = 11;
 cmd.Parameters.Add(paramSSN);
 using (SqlDataReader reader = cmd.ExecuteReader())
 {
   if (reader.HasRows)
 {
 while (reader.Read())
 {
    Console.WriteLine(@"{0}, {1}, {2}, {3}", reader[0], reader[1], reader[2], ((DateTime)reader[3]).ToShortDateString());
 }
```

### <a name="retrieving-encrypted-data-example"></a>Пример получения зашифрованных данных

Если постоянное шифрование не включено, запрос может получать данные из зашифрованных столбцов, пока для него не будут указаны параметры, предназначенные для зашифрованных столбцов.

В следующем примере показано извлечение двоичных зашифрованных данных из зашифрованных столбцов. Следует отметить следующее.

- Так как постоянное шифрование не включено в строке подключения, запрос будет возвращать зашифрованные значения SSN и BirthD в виде байтовых массивов (программа преобразует значения в строки).
- Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Приведенный выше запрос выполняет фильтрацию по LastName, который не зашифрован в базе данных. Запрос, отфильтрованный по SSN или BirthDate, завершится ошибкой.


```cs
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true";
                
using (SqlConnection connection = new SqlConnection(connectionString))
{
   connection.Open();
   using (SqlCommand cmd = connection.CreateCommand())
   {
      cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName]=@LastName";
      SqlParameter paramLastName = cmd.CreateParameter();
      paramLastName.ParameterName = @"@LastName";
      paramLastName.DbType = DbType.String;
      paramLastName.Direction = ParameterDirection.Input;
      paramLastName.Value = "Abel";
      paramLastName.Size = 50;
      cmd.Parameters.Add(paramLastName);
      using (SqlDataReader reader = cmd.ExecuteReader())
      {
         if (reader.HasRows)
         {
            while (reader.Read())
         {
         Console.WriteLine(@"{0}, {1}, {2}, {3}", BitConverter.ToString((byte[])reader[0]), reader[1], reader[2], BitConverter.ToString((byte[])reader[3]));
      }
   }
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Как избежать распространенных проблем при запросе зашифрованных столбцов

В этом разделе описываются общие категории ошибок, возникающих при выполнении запросов к зашифрованным столбцам из приложений .NET, и приводятся рекомендации о том, как их избежать.

### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования неподдерживаемых типов данных

Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. Подробный список поддерживаемых преобразований типов см. в статье [Always Encrypted](always-encrypted-database-engine.md). Чтобы избежать ошибок при преобразовании типов данных, сделайте следующее:

- Задайте типы параметров, предназначенных для зашифрованных столбцов, так, чтобы тип данных SQL Server параметра точно совпадал с типом целевого столбца или чтобы поддерживалось преобразование типа данных SQL Server параметра в целевой тип столбца. С помощью свойства SqlParameter.SqlDbType можно принудительно задать нужное сопоставление типов данных .NET с конкретными типами данных SQL Server.
- Убедитесь, что точность и масштаб параметров, предназначенных для столбцов типов данных SQL Server decimal и numeric, соответствуют точности и масштабу, настроенным для целевого столбца.  
- Убедитесь, что точность параметров, предназначенных для столбцов типов данных SQL Server datetime2, datetimeoffset или time, не превышает точность для целевого столбца (в запросах, которые изменяют значения целевого столбца).  

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки, возникающие из-за передачи значений в виде открытого текста, а не в зашифрованном виде

Любое значение, предназначенное для зашифрованного столбца, должно быть зашифровано внутри приложения. Попытка вставки, изменения или фильтрации по значению в виде открытого текста в зашифрованном столбце приведет к возникновению ошибки, подобной следующей:


```cs
System.Data.SqlClient.SqlException (0x80131904): Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'CEK_Auto1', column_encryption_key_database_name = 'Clinic') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Чтобы избежать таких ошибок, убедитесь, что:
- функция Always Encrypted включена для запросов приложений, предназначенных для зашифрованных столбцов (для строки подключения или в отдельном объекте [SqlCommand](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommand.aspx) для конкретного запроса);
- для отправки данных, предназначенных для зашифрованных столбцов, используется параметр SqlParameter. В примере ниже показан запрос, который вместо передачи литерала внутри объекта SqlParameter неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN). 


```cs
using (SqlCommand cmd = connection.CreateCommand())
{
   cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
cmd.ExecuteNonQuery();
}
```

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главных ключей столбцов

Чтобы зашифровать значение параметра или расшифровать данные в результатах запроса, поставщику данных .NET Framework для SQL Server необходимо получить ключ шифрования столбца, настроенный для целевого столбца. Ключи шифрования столбцов хранятся в зашифрованном виде в метаданных базы данных. Каждый ключ шифрования столбца имеет соответствующий главный ключ столбца, который использовался для шифрования ключа шифрования столбца. Метаданные базы данных не хранят главные ключи столбцов — они содержат только сведения о хранилище ключей, где находится определенный главный ключ столбца, и расположении ключа в хранилище ключей.

Чтобы получить значение в виде открытого текста для ключа шифрования столбца, поставщик данных .NET Framework для SQL Server сначала получает метаданные о ключе шифрования столбца и соответствующем ему главном ключе столбца, а затем использует сведения в метаданных для доступа в хранилище ключей, содержащее главный ключ столбца, и для расшифровки ключа шифрования зашифрованных столбцов. Поставщик данных .NET Framework для SQL Server взаимодействует с хранилищем ключей с помощью поставщика хранилища главных ключей столбцов, который является экземпляром класса, производным от класса [SqlColumnEncryptionKeyStoreProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptionkeystoreprovider.aspx).


Процедура получения ключа шифрования столбца:

1.  Если Always Encrypted включено для запроса, поставщик данных .NET Framework для SQL Server прозрачно вызывает **sys.sp_describe_parameter_encryption** , чтобы получить метаданные шифрования для параметров, предназначенных для зашифрованных столбцов, если запрос содержит параметры. Для зашифрованных данных, содержащихся в результатах запроса, SQL Server автоматически присоединяет метаданные шифрования. Сведения о главном ключе столбца включают в себя следующее:
    - Имя поставщика хранилища ключей, который инкапсулирует хранилище ключей, содержащее главный ключ столбца. 
    - Путь к ключу, указывающий положение главного ключа столбца в хранилище ключей.
    
    Сведения о ключе шифрования столбца включают в себя следующее:

    - Зашифрованное значение ключа шифрования столбца.
    - Имя алгоритма, который использовался для шифрования ключа шифрования столбца.
2.  Поставщик данных .NET Framework для SQL Server использует имя поставщика хранилища главных ключей столбцов для поиска объекта поставщика (экземпляр класса, производного от класса SqlColumnEncryptionKeyStoreProvider) во внутренней структуре данных.
3.  Чтобы расшифровать ключ шифрования столбца, поставщик данных .NET Framework для SQL Server вызывает метод SqlColumnEncryptionKeyStoreProvider.DecryptColumnEncryptionKey, передавая путь к главному ключу столбца, зашифрованное значение ключа шифрования столбца и имя алгоритма шифрования, используемого для создания ключа шифрования зашифрованных столбцов.




### <a name="using-built-in-column-master-key-store-providers"></a>Использование встроенных поставщиков хранилища главных ключей столбцов

В состав поставщика данных .NET Framework для SQL Server входят следующие встроенные поставщики хранилища главных ключей столбцов, которые предварительно зарегистрированы с конкретными именами поставщиков (используемыми для поиска поставщика).


| Class | Описание | Имя поставщика |
|:---|:---|:---|
|Класс SqlColumnEncryptionCertificateStoreProvider| Поставщик для хранилища сертификатов Windows. | MSSQL_CERTIFICATE_STORE |
|[Класс SqlColumnEncryptionCngProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx) <br><br>**Примечание.** Этот поставщик доступен в .NET Framework 4.6.1 или более поздней версии. |Поставщик хранилища ключей, поддерживающий [Microsoft Cryptography API: Next Generation (CNG) API](https://msdn.microsoft.com/library/windows/desktop/aa376210.aspx). Как правило, такое хранилище представляет собой аппаратный модуль безопасности — физическое устройство, которое защищает цифровые ключи и управляет ими, а также обеспечивает обработку шифрования.  | MSSQL_CNG_STORE|
| [Класс SqlColumnEncryptionCspProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncspprovider.aspx)<br><br>**Примечание.** Этот поставщик доступен в .NET Framework 4.6.1 или более поздней версии.| Поставщик хранилища ключей, поддерживающий [Microsoft Cryptography API (CAPI)](https://msdn.microsoft.com/library/aa266944.aspx). Как правило, такое хранилище представляет собой аппаратный модуль безопасности — физическое устройство, которое защищает цифровые ключи и управляет ими, а также обеспечивает обработку шифрования.| MSSQL_CSP_PROVIDER |
  
Для использования этих поставщиков не требуется изменять код приложения, однако необходимо учесть следующие моменты.

- Вы (или ваш администратор баз данных) должны проверить правильность имени поставщика, настроенного в метаданных главного ключа столбца, и убедиться, что путь к ключу главного ключа столбца соответствует формату пути к ключу, который является допустимым для данного поставщика. Для настройки ключей рекомендуется использовать средство, такое как среда SQL Server Management Studio, которое при выполнении инструкции [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md) автоматически создает допустимые имена поставщиков и пути к ключам. Дополнительные сведения см. в разделах [Configuring Always Encrypted using SQL Server Management Studio](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md) (Настройка Always Encrypted с помощью среды SQL Server Management Studio ) и [Настройка постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md).
- Убедитесь, что приложение может получить доступ к ключу в хранилище ключей. Для этого может потребоваться предоставить приложению доступ к ключу или хранилищу ключей (в зависимости от хранилища ключей) или выполнить другие действия по настройке конкретного хранилища ключей. Например, для доступа к хранилищу, реализующему CNG или CAPI (например, к аппаратному модулю безопасности), на компьютере с приложением необходимо установить библиотеку, реализующую CNG или CAPI для хранилища. Дополнительные сведения см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

### <a name="using-azure-key-vault-provider"></a>Использование поставщика хранилища ключей Azure

Хранилище ключей Azure удобно для хранения главных ключей столбцов для постоянного шифрования, особенно в том случае, если приложения размещены в Azure. Поставщик данных .NET Framework для SQL Server не содержит встроенный поставщик хранилища главных ключей столбцов для хранилища ключей Azure, но он доступен как пакет Nuget, который можно легко интегрировать в приложение. Дополнительные сведения см. в статье [Постоянное шифрование: защита конфиденциальных данных в базе данных SQL с помощью шифрования базы данных и хранение ключей шифрования в хранилище ключей Azure](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted-azure-key-vault/).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Реализация настраиваемого поставщика хранилища главных ключей столбцов

Чтобы сохранить главные ключи столбцов в хранилище ключей, не поддерживаемом существующим поставщиком, можно реализовать настраиваемый поставщик, расширив [класс SqlColumnEncryptionCngProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx) и зарегистрировав поставщик с помощью метода [SqlConnection.RegisterColumnEncryptionKeyStoreProviders](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.registercolumnencryptionkeystoreproviders.aspx) .


```cs
public class MyCustomKeyStoreProvider : SqlColumnEncryptionKeyStoreProvider
    {
        public override byte[] EncryptColumnEncryptionKey(string masterKeyPath, string encryptionAlgorithm, byte[] columnEncryptionKey)
        {
            // Logic for encrypting a column encrypted key.
        }
        public override byte[] DecryptColumnEncryptionKey(string masterKeyPath, string encryptionAlgorithm, byte[] EncryptedColumnEncryptionKey)
        {
            // Logic for decrypting a column encrypted key.
        }
    }  
    class Program
    {
        static void Main(string[] args)
        {
            Dictionary\<string, SqlColumnEncryptionKeyStoreProvider> providers =
               new Dictionary\<string, SqlColumnEncryptionKeyStoreProvider>();
            providers.Add("MY_CUSTOM_STORE", customProvider);
            SqlConnection.RegisterColumnEncryptionKeyStoreProviders(providers);
            providers.Add(SqlColumnEncryptionCertificateStoreProvider.ProviderName, customProvider);
            SqlConnection.RegisterColumnEncryptionKeyStoreProviders(providers); 
       // ...
        }

    }
```
 
### <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Использование поставщиков хранилищ главных ключей столбцов для программной подготовки ключей

При доступе к зашифрованным столбцам поставщик данных .NET Framework для SQL Server прозрачно находит и вызывает нужный поставщик хранилища главных ключей столбцов, чтобы расшифровать ключи шифрования столбцов. Как правило, обычный код приложения не вызывает поставщики хранилища главных ключей напрямую. Однако можно создать и явным образом вызвать поставщик для программной подготовки ключей постоянного шифрования и управления ими: для создания ключа шифрования зашифрованного столбца и расшифровки ключа шифрования столбца (например, в ходе смены главного ключа столбца). Дополнительные сведения см. в разделе [Общие сведения об управлении ключами для Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).
Реализация собственных средств управления ключами может потребоваться только в том случае, если используется настраиваемый поставщик хранилища ключей. При использовании ключей, хранящихся в хранилище ключей, для которых существует встроенный поставщик, или в хранилище ключей Azure для управления ключами и их подготовки можно применять существующие средства, такие как SQL Server Management Studio или PowerShell.
В примере ниже показано создание ключа шифрования столбца и использование [класса SqlColumnEncryptionCertificateStoreProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncertificatestoreprovider.aspx) для шифрования ключа с помощью сертификата.


```cs
using System.Security.Cryptography;
static void Main(string[] args)
{
    byte[] EncryptedColumnEncryptionKey = GetEncryptedColumnEncryptonKey(); 
    Console.WriteLine("0x" + BitConverter.ToString(EncryptedColumnEncryptionKey).Replace("-", "")); 
    Console.ReadKey();
}

static byte[]  GetEncryptedColumnEncryptonKey()
{
    int cekLength = 32;
    String certificateStoreLocation = "CurrentUser";
    String certificateThumbprint = "698C7F8E21B2158E9AED4978ADB147CF66574180";
    // Generate the plaintext column encryption key.
    byte[] columnEncryptionKey = new byte[cekLength];
    RNGCryptoServiceProvider rngCsp = new RNGCryptoServiceProvider();
    rngCsp.GetBytes(columnEncryptionKey);

    // Encrypt the column encryption key with a certificate.
    string keyPath = String.Format(@"{0}/My/{1}", certificateStoreLocation, certificateThumbprint);
    SqlColumnEncryptionCertificateStoreProvider provider = new SqlColumnEncryptionCertificateStoreProvider();
    return provider.EncryptColumnEncryptionKey(keyPath, @"RSA_OAEP", columnEncryptionKey); 
}
```


## <a name="controlling-performance-impact-of-always-encrypted"></a>Управление влиянием постоянного шифрования на производительность

Поскольку постоянное шифрование является технологией шифрования на стороне клиента, значительное влияние на производительность происходит на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и расшифровки существуют и другие источники снижения производительности на стороне клиента:
- Дополнительные обращения к базе данных для получения метаданных для параметров запроса.
- Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.

В этом разделе описываются процессы оптимизации производительности, встроенные в поставщик .NET Framework для SQL Server, и способы управления влиянием двух указанных выше факторов на производительность.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Управление обращениями для получения метаданных для параметров запроса

Если для соединения включена функция Always Encrypted, по умолчанию поставщик данных .NET Framework для SQL Server будет вызывать [sys.sp_describe_parameter_encryption](../../system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) для каждого параметризованного запроса, передавая инструкцию запроса (без значений параметров) в SQL Server. **sys.sp_describe_parameter_encryption** анализирует инструкцию запроса и для каждого параметра, который должен быть зашифрован, возвращает связанные с шифрованием сведения, позволяющие поставщику данных .NET Framework для SQL Server шифровать значения параметров. Описанное выше поведение обеспечивает высокий уровень прозрачности для клиентского приложения. Пока значения, предназначенные для зашифрованных столбцов, передаются поставщику данных .NET Framework для SQL Server в объектах SqlParameter, приложению (и разработчику приложений) не требуется знать, какие запросы получают доступ к зашифрованным столбцам.


### <a name="query-metadata-caching"></a>Кэширование метаданных запроса

В платформе .NET Framework 4.6.2 и более поздней версии поставщик данных .NET Framework для SQL Server кэширует результаты **sys.sp_describe_parameter_encryption** для каждой инструкции запроса. Следовательно, если одна и та же инструкция запроса выполняется несколько раз, драйвер вызывает **sys.sp_describe_parameter_encryption** всего один раз. Кэширование метаданных шифрования для инструкций запроса значительно сокращает затраты ресурсов на получение метаданных из базы данных. Кэширование включено по умолчанию. Можно отключить параметр кэширования метаданных, задав для [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled свойство](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionquerymetadatacacheenabled.aspx) значение false, однако рекомендуется делать это только в редких случаях, например в описанной ниже ситуации:

Рассмотрим базу данных с двумя различными схемами: s1 и s2. Каждая схема содержит таблицу с одинаковым именем: t. Определения таблиц s1.t и s2.t идентичны за исключением свойств, связанных с шифрованием: столбец с именем "c" в таблице s1.t не шифруется, но он зашифрован в таблице s2.t. База данных имеет двух пользователей: u1 и u2. Схема по умолчанию для пользователя u1 — s1. Схема по умолчанию для u2 — s2. Приложения .NET открывает два подключения к базе данных, олицетворяя пользователя u1 в одном соединении и пользователя u2 в другом. Приложение отправляет запрос с параметром, предназначенным для столбца c, через соединение для пользователя u1 (запрос не указывает схему, поэтому подразумевается схема пользователя по умолчанию). Затем приложение отправляет тот же запрос через соединение для пользователя u2. Если кэширование метаданных запроса включено, после первого запроса кэш заполняется метаданными, указывающими, что столбец c, для которого предназначен параметр запроса, не шифруются. Так как второй запрос такую же инструкцию запроса, используются сведения, хранящиеся в кэше. В результате драйвер посылает запрос без шифрования параметра (что неверно, так как целевой столбец s2.t.c шифруется), в результате чего происходит утечка значения параметра в формате открытого текста на сервер. Сервер обнаружит несоответствие и велит драйверу обновить кэш, чтобы приложение могло прозрачно переотправить запрос с правильно зашифрованным значением параметра. В этом случае следует отключить кэширование во избежание утечки конфиденциальных значений на сервер. 




### <a name="setting-always-encrypted-at-the-query-level"></a>Задание постоянного шифрования на уровне запроса

Для управления влиянием процесса получения метаданных шифрования для параметризованных запросов на производительность можно включить постоянное шифрование для отдельных запросов, а не настраивать его для соединения. Таким образом, это гарантирует, что **sys.sp_describe_parameter_encryption** вызывается только для запросов, которые точно имеют параметры, предназначенные для зашифрованных столбцов. Обратите внимание, что в этом случае снижается прозрачность шифрования: при изменении свойств шифрования столбцов базы данных может потребоваться изменить код приложения в соответствии с изменениями схемы.

> [!NOTE]
> Настройка Always Encrypted на уровне запроса дает ограниченный выигрыш в производительности для платформы .NET 4.6.2 и более поздних версий, где реализовано кэширование метаданных шифрования параметра.

Для управления поведением функции Always Encrypted в отдельных запросах необходимо использовать этот конструктор [SqlCommand](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommand.aspx) и [SqlCommandColumnEncryptionSetting](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommandcolumnencryptionsetting.aspx). Ниже приведены некоторые полезные рекомендации.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, получает доступ к зашифрованным столбцам:
    - Задайте для ключевого слова строки подключения **Параметр шифрования столбца** значение *Включено*.
    - Задайте **SqlCommandColumnEncryptionSetting.Disabled** для отдельных запросов, которые не обращаются к зашифрованным столбцам. Будет отключена возможность вызова sys.sp_describe_parameter_encryption и расшифровки всех значений в наборе результатов.
    - Задайте **SqlCommandColumnEncryptionSetting.ResultSet** для отдельных запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, не получают доступа к зашифрованным столбцам:
    - Задайте для ключевого слова строки подключения **Параметр шифрования столбца** значение **Отключено**.
    - Задайте **SqlCommandColumnEncryptionSetting.Enabled** для отдельных запросов, имеющих параметры, которые требуется зашифровать. Будет включена возможность вызова sys.sp_describe_parameter_encryption и расшифровки результатов запроса, полученных из зашифрованных столбцов.
    - Задайте **SqlCommandColumnEncryptionSetting.ResultSet** для запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.

В следующем примере постоянное шифрование отключено для подключения к базе данных. Запрос, выполняемый приложением, имеет параметр, предназначенный для незашифрованного столбца LastName. Запрос получает данные из зашифрованных столбцов SSN и BirthDate. В этом случае вызывать sys.sp_describe_parameter_encryption для получения метаданных шифрования не требуется. Однако необходимо включить расшифровку результатов запроса, чтобы приложение могло получать значения в виде обычного текста из двух зашифрованных столбцов. Для этого используется параметр SqlCommandColumnEncryptionSetting.ResultSet.



```cs
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true";
using (SqlConnection connection = new SqlConnection(connectionString))
{
    connection.Open();
    using (SqlCommand cmd = new SqlCommand(@"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName]=@LastName",
connection, null, SqlCommandColumnEncryptionSetting.ResultSetOnly))
    {
        SqlParameter paramLastName = cmd.CreateParameter();
        paramLastName.ParameterName = @"@LastName";
        paramLastName.DbType = DbType.String;
        paramLastName.Direction = ParameterDirection.Input;
        paramLastName.Value = "Abel";
        paramLastName.Size = 50;
        cmd.Parameters.Add(paramLastName);
        using (SqlDataReader reader = cmd.ExecuteReader())
            {
               if (reader.HasRows)
               {
                  while (reader.Read())
                  {
                     Console.WriteLine(@"{0}, {1}, {2}, {3}", reader[0], reader[1], reader[2], ((DateTime)reader[3]).ToShortDateString());
                  }
               }
            }
  } 
}
```


### <a name="column-encryption-key-caching"></a>Кэширование ключа шифрования столбца

Чтобы уменьшить количество вызовов к хранилищу главных ключей столбцов для расшифровки ключей шифрования столбцов, поставщик данных .NET Framework для SQL Server кэширует ключи шифрования столбцов с открытым текстом в памяти. После получения значения ключа шифрования зашифрованного столбца метаданных базы данных драйвер сначала пытается найти ключ шифрования столбца с открытым текстом, соответствующий зашифрованному значению ключа. Драйвер обращается к хранилищу ключей, содержащему главный ключ столбца, только в том случае, если ему не удается найти значение ключа шифрования зашифрованных столбцов в кэше.

> [!NOTE]
> В платформе .NET Framework 4.6 и 4.6.1 записи ключей шифрования столбцов в кэше никогда не удаляются. Это означает, что для данного ключа шифрования зашифрованного столбца драйвер обращается в хранилище ключей только один раз за все время существования приложения.

В платформе .NET Framework 4.6.2 и более поздних версий записи кэша удаляются по истечении настроенного срока жизни из соображений безопасности. Значение по умолчанию для срока жизни составляет 2 часа. Если у вас действуют более строгие требования к безопасности, касающиеся времени кэширования ключей шифрования столбца в виде открытого текста в приложении, это значение можно изменить с помощью [свойства SqlConnection.ColumnEncryptionKeyCacheTtl](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionkeycachettl.aspx). 


## <a name="enabling-additional-protection-for-a-compromised-sql-server"></a>Включение дополнительной защиты для скомпрометированного SQL Server

По умолчанию *поставщик данных .NET Framework для SQL Server* полагается на систему базы данных (SQL Server или Базу данных SQL Azure), которая предоставляет метаданные о том, какие столбцы базы данных шифруются и как именно. Метаданные шифрования позволяют поставщику данных .NET Framework для SQL Server шифровать параметры запроса и расшифровывать результаты запроса без получения дополнительных входных данных из приложения, что позволяет значительно сократить число изменений, необходимых для приложения. Однако если процесс SQL Server скомпрометирован и злоумышленник незаконно изменяет метаданные, которые SQL Server отправляет поставщику данных платформы .NET Framework для SQL Server, злоумышленник получает возможность украсть конфиденциальную информацию. В этом разделе описываются интерфейсы API, которые помогают обеспечить дополнительный уровень защиты от таких атак за счет снижения прозрачности. 

### <a name="forcing-parameter-encryption"></a>Принудительное шифрование параметров 

Прежде чем поставщик данных .NET Framework для SQL Server отправляет параметризованный запрос в SQL Server, он просит SQL Server (путем вызова [sys.sp_describe_parameter_encryption](../../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)) проанализировать инструкцию запроса и предоставить сведения о том, какие параметры запроса должны быть зашифрованы. Скомпрометированный экземпляр SQL Server может ввести поставщика данных .NET Framework для SQL Server в заблуждение, отправляя метаданные о том, что параметр не предназначен для зашифрованного столбца, хотя этот столбец в базе данных шифруется. В результате поставщик данных .NET Framework для SQL Server не шифрует значение параметра и отправляет его в формате открытого текста в скомпрометированный экземпляр SQL Server.

Чтобы предотвратить подобную атаку, приложение может присвоить [свойству SqlParameter.ForceColumnEncryption](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.forcecolumnencryption.aspx) для параметра значение true. Это приводит к тому, что поставщик данных .NET Framework для SQL Server выдает исключение, если полученные им с сервера метаданные указывают, что шифровать параметр не нужно.

Хотя использование **свойства SqlParameter.ForceColumnEncryption** помогает повысить безопасность, оно также снижает прозрачность шифрования для клиентского приложения. Если вы обновляете схему базы данных для изменения набора зашифрованных столбцов, вам может потребоваться изменить и само приложение.

В следующем примере кода показано, как с помощью **свойства SqlParameter.ForceColumnEncryption** предотвратить отправку номеров социального страхования в базу данных в формате открытого текста. 



```cs
SqlCommand cmd = _sqlconn.CreateCommand(); 

// Use parameterized queries to access Always Encrypted data. 
 
cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = @SSN;"; 

SqlParameter paramSSN = cmd.CreateParameter(); 
paramSSN.ParameterName = @"@SSN"; 
paramSSN.DbType = DbType.AnsiStringFixedLength; 
paramSSN.Direction = ParameterDirection.Input; 
paramSSN.Value = ssn; 
paramSSN.Size = 11; 
paramSSN.ForceColumnEncryption = true; 
cmd.Parameters.Add(paramSSN); 

SqlDataReader reader = cmd.ExecuteReader();
```
 

### <a name="configuring-trusted-column-master-key-paths"></a>Настройка доверенных путей для главных ключей столбцов 

Метаданные шифрования, возвращаемые SQL Server для параметров запроса, предназначенных для зашифрованных столбцов, и результатов, полученных из зашифрованных столбцов, включают в себя путь к главному ключу столбца, определяющий хранилище ключей и расположение ключа в этом хранилище. Если экземпляр SQL Server скомпрометирован, он может отправить путь к ключу, указывающий на поставщик данных .NET Framework для SQL Server в расположении, контролируемом злоумышленником. Это может привести к утечке учетных данных хранилища ключей, если оно запрашивает у приложение прохождение проверки подлинности. 

Для предотвращения подобных атак приложение может задать список доверенных путей для отдельного сервера с помощью [свойства SqlConnection.ColumnEncryptionTrustedMasterKeyPaths](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptiontrustedmasterkeypaths.aspx). Если поставщик данных платформы.NET для SQL Server получает путь, не входящий в доверенный список, он выдает исключение. 

Несмотря на то, что установка доверенных путей повышает безопасность приложения, вам потребуется изменять код или (и) конфигурацию приложения при каждой смене главного ключа столбца (или при изменении пути к главному ключу столбца). 

В следующем примере показано, как настраивать доверенные пути к главному ключу столбца:


```cs
// Configure trusted key paths to protect against fake key paths sent by a compromised SQL Server instance 
// First, create a list of trusted key paths for your server 
List<string> trustedKeyPathList = new List<string>(); 
trustedKeyPathList.Add("CurrentUser/my/425CFBB9DDDD081BB0061534CE6AB06CB5283F5Ea"); 

// Register the trusted key path list for your server 

SqlConnection.ColumnEncryptionTrustedMasterKeyPaths.Add(serverName, trustedKeyPathList);
```
 



## <a name="copying-encrypted-data-using-sqlbulkcopy"></a>Копирование зашифрованных данных с помощью SqlBulkCopy

С помощью SqlBulkCopy можно скопировать данные, которые уже зашифрованы и хранятся в одной таблице, в другую таблицу, не расшифровывая при этом данные. Для этого выполните указанные далее действия.

- Убедитесь, что конфигурация шифрования целевой таблицы идентична конфигурации исходной таблицы. В частности, обе таблицы должны иметь одинаковые зашифрованные столбцы, которые должны быть зашифрованы с помощью одних и тех же типов шифрования и ключей шифрования. Примечание. Если способ шифрования какого-либо целевого столбца отличается от способа шифрования соответствующего исходного столбца, вы не сможете расшифровать данные в целевой таблице после операции копирования. Данные будут повреждены.
- Настройте подключения базы данных к исходной и целевой таблицам без включения постоянного шифрования. 
- Задайте параметр AllowEncryptedValueModifications (см. раздел [SqlBulkCopyOptions](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopyoptions.aspx)). Примечание. Будьте внимательны при указании параметра AllowEncryptedValueModifications, так как это может привести к повреждению базы данных, поскольку поставщик данных .NET Framework для SQL Server не проверяет необходимость шифрования данных или правильность их шифрования с помощью того же типа шифрования, алгоритма и ключа, как для целевого столбца.

Параметр AllowEncryptedValueModifications доступен в .NET Framework 4.6.1 и более поздних версиях.

Ниже приведен пример копирования данных из одной таблицы в другую. Предполагается, что столбцы SSN и BirthDate зашифрованы.
        

```cs
static public void CopyTablesUsingBulk(string sourceTable, string targetTable)
{
   string sourceConnectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true";
   string targetConnectionString = "Data Source= server64; Initial Catalog=Clinic; Integrated Security=true";
   using (SqlConnection connSource = new SqlConnection(sourceConnectionString))
   {
      connSource.Open();
      using (SqlCommand cmd = new SqlCommand(string.Format("SELECT [PatientID], [SSN], [FirstName], [LastName], [BirthDate] FROM {0}", sourceTable), connSource))
      {
         using (SqlDataReader reader = cmd.ExecuteReader())
         {
            SqlBulkCopy copy = new SqlBulkCopy(targetConnectionString, SqlBulkCopyOptions.KeepIdentity | SqlBulkCopyOptions.AllowEncryptedValueModifications);
            copy.EnableStreaming = true;
            copy.DestinationTableName = targetTable;
            copy.WriteToServer(reader);
         }
      }
}
```


## <a name="always-encrypted-api-reference"></a>Справочник по API Always Encrypted

**Пространство имен:** [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx)

**Сборка**: System.Data (в System.Data.dll)




|Имя|Описание|Версия .NET
|:---|:---|:---
|[Класс SqlColumnEncryptionCertificateStoreProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncertificatestoreprovider.aspx)|Поставщик хранилища ключей для хранилища сертификатов Windows.|  4.6
|[Класс SqlColumnEncryptionCngProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx)|Поставщик хранилища ключей для интерфейса Microsoft Cryptography API: Next Generation (CNG).|  4.6.1
|[Класс SqlColumnEncryptionCspProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncspprovider.aspx)|Поставщик хранилища ключей для Microsoft CAPI на основе поставщиков служб шифрования (CSP).|4.6.1  
|[SqlColumnEncryptionKeyStoreProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptionkeystoreprovider.aspx)|Базовый класс для всех поставщиков хранилища ключей.|  4.6
|[Перечисление SqlCommandColumnEncryptionSetting](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommandcolumnencryptionsetting.aspx)|Параметры для включения шифрования и расшифровки для подключения к базе данных.|4.6  
|[Перечисление SqlCommandColumnEncryptionSetting](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnectioncolumnencryptionsetting.aspx)|Параметры для управления поведением постоянного шифрования для отдельных запросов.|4.6  
| [Свойство SqlConnectionStringBuilder.ColumnEncryptionSetting](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnectionstringbuilder.columnencryptionsetting.aspx)|Возвращает и задает постоянное шифрование в строке подключения.|4.6|
| [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled свойство](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionquerymetadatacacheenabled.aspx) | Включает и отключает кэширование метаданных для запроса шифрования. | 4.6.2
| [свойства SqlConnection.ColumnEncryptionKeyCacheTtl](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionkeycachettl.aspx) | Возвращает и задает срок жизни для записей в кэше ключа шифрования столбца. | 4.6.2
|[свойства SqlConnection.ColumnEncryptionTrustedMasterKeyPaths](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptiontrustedmasterkeypaths.aspx)|Позволяет задать список доверенных путей ключа для сервера базы данных. Если при обработке запроса приложения драйвер получает путь ключа, которого нет в списке, запрос завершается с ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление скомпрометированным SQL Server фиктивных путей ключа, что может привести к утечке учетных данных хранилища ключей.|  4.6
|[Метод SqlConnection.RegisterColumnEncryptionKeyStoreProviders](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.registercolumnencryptionkeystoreproviders.aspx)|Позволяет регистрировать пользовательские поставщики хранилища ключей. Это словарь, сопоставляющий имена поставщиков хранилища ключей с реализациями поставщиков хранилища ключей.|  4.6
|[Конструктор SqlCommand (String, SqlConnection, SqlTransaction, SqlCommandColumnEncryptionSetting)](https://msdn.microsoft.com/library/dn956511\(v=vs.110\).aspx)|Позволяет управлять поведением постоянного шифрования для отдельных запросов.|  4.6
|[свойству SqlParameter.ForceColumnEncryption](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.forcecolumnencryption.aspx)|Принудительно шифрует параметр. Если SQL Server сообщает драйверу, что параметр не должен быть зашифрован, запрос, использующий параметр, завершится ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление клиенту скомпрометированным SQL Server неверных метаданных шифрования, что может привести к раскрытию данных.|4.6  
|Новое ключевое слово [строки подключения](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx) : `Column Encryption Setting=enabled`|Включает или отключает функцию постоянного шифрования для подключения.| 4.6 
  

## <a name="see-also"></a>См. также:

- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Блог о постоянном шифровании](https://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)
- [Учебник по базе данных SQL: защита конфиденциальных данных с помощью Always Encrypted](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/)

















