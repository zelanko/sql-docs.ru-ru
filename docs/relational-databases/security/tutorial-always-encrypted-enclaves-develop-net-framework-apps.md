---
title: Руководство по Разработка приложения .NET Framework с помощью Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 62c4954663f7553fd6df7461f5b5c967f7386721
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279360"
---
# <a name="tutorial-develop-a-net-framework-application-using-always-encrypted-with-secure-enclaves"></a>Руководство по Разработка приложения .NET Framework с помощью Always Encrypted с безопасными анклавами
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

В этом руководстве содержатся сведения о разработке простого приложения, которое выполняет запросы к базе данных, использующие безопасный анклав на стороне сервера для [Always Encrypted с защищенными анклавами](encryption/always-encrypted-enclaves.md). 

## <a name="prerequisites"></a>Предварительные требования
Это руководство представляет собой продолжение статьи [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](./tutorial-getting-started-with-always-encrypted-enclaves.md). Убедитесь, что вы полностью изучили его, прежде чем выполнять действия ниже.

Кроме того, требуется среда Visual Studio (рекомендуется версия 2019), которую можно скачать на странице [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com). На компьютере для разработки приложений должна быть установлена платформа .NET Framework 4.7.2 или более поздней версии.

## <a name="step-1-set-up-your-visual-studio-project"></a>Шаг 1. Настройка проекта в Visual Studio

Чтобы использовать функцию Always Encrypted с безопасными анклавами в приложении .NET Framework, вам нужно убедиться в том, что приложение создано на основе .NET Framework 4.7.2 и интегрировано с [пакетом NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders). Кроме того, если вы храните главный ключ столбца в Azure Key Vault, необходимо также интегрировать приложение с [пакетом NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) версии 2.2.0 или более поздней. 

1. Запустите Visual Studio.

2. Создайте проект консольного приложения C\# (.NET Framework).

3. Убедитесь, что в проекте настроена по крайней мере платформа .NET Framework 4.7.2. Щелкните правой кнопкой мыши проект в обозревателе решений, выберите "Свойства" и установите целевую платформу. NET Framework 4.7.2.

4. Установите следующий пакет NuGet. Щелкните **Инструменты** (главное меню) > **Диспетчер пакетов NuGet** > **Консоль диспетчера пакетов**. Выполните следующий код в консоли диспетчера пакетов.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders -IncludePrerelease
   ```

5. Если вы используете Azure Key Vault для хранения главных ключей столбцов, установите следующие пакеты NuGet, щелкнув **Инструменты** (главное меню) > **Диспетчер пакетов NuGet** > **Консоль диспетчера пакетов**. Выполните следующий код в консоли диспетчера пакетов.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -IncludePrerelease -Version 2.2.0
   Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
   ```

7. Откройте файл App.config для проекта.

8. Откройте раздел \<configuration\> и добавьте или обновите разделы \<configSections\>.

   а. Если в разделе \<configuration\> **нет** раздела \<configSections\>, добавьте приведенное ниже содержимое сразу после раздела \<configuration\>.
   
      ```xml
      <configSections>
         <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
      </configSections>
      ```
   b. Если раздел \<configruation\> уже содержит раздел \<configSections\>, добавьте следующую строку в раздел \<configSections\>:

   ```xml
   <section name="SqlColumnEncryptionEnclaveProviders"  type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data,  Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
   ```

9. В разделе конфигурации под \<configSections\> добавьте следующий раздел, в котором указан поставщик анклава, который будет использоваться для подтверждения анклавов VBS и взаимодействия с ними:

   ```xml
   <SqlColumnEncryptionEnclaveProviders>
       <providers>
           <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
       </providers>
   </SqlColumnEncryptionEnclaveProviders>
   ```

Ниже представлен полный пример файла app.config для простого консольного приложения.
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
    </providers>
  </SqlColumnEncryptionEnclaveProviders>
  <startup> 
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.2" />
  </startup>
</configuration>
```
## <a name="step-2-implement-your-application-logic"></a>Шаг 2. Реализация логики приложения
Приложение подключится к базе данных **ContosoHR** из статьи [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](tutorial-getting-started-with-always-encrypted-enclaves.md) и выполнит запрос, содержащий предикат `LIKE` в столбце **SSN**, а также проведет сравнение диапазонов в столбце **Salary**.

1. Замените содержимое файла Program.cs (созданного в Visual Studio) на приведенный ниже код. Обновите строку подключения к базе данных, указав имя сервера и URL-адрес аттестации анклава для своей среды. Можно также изменить параметры проверки подлинности базы данных.

    ```cs
    using System;
    using System.Data.SqlClient;
    using System.Data;

    namespace ConsoleApp1
    {
        class Program
        {
            static void Main(string[] args)
            {
    
                string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = http://hgs.bastion.local/Attestation; Integrated Security = true";

                using (SqlConnection connection = new SqlConnection(connectionString))
                {
                    connection.Open();

                    SqlCommand cmd = connection.CreateCommand();
                    cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";

                    SqlParameter paramSSNPattern = cmd.CreateParameter();

                    paramSSNPattern.ParameterName = @"@SSNPattern";
                    paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
                    paramSSNPattern.Direction = ParameterDirection.Input;
                    paramSSNPattern.Value = "%1111";
                    paramSSNPattern.Size = 11;

                    cmd.Parameters.Add(paramSSNPattern);

                    SqlParameter MinSalary = cmd.CreateParameter();

                    MinSalary.ParameterName = @"@MinSalary";
                    MinSalary.DbType = DbType.Currency;
                    MinSalary.Direction = ParameterDirection.Input;
                    MinSalary.Value = 900;

                    cmd.Parameters.Add(MinSalary);
                    cmd.ExecuteNonQuery();
    
                    SqlDataReader reader = cmd.ExecuteReader();
                    while (reader.Read())

                    {
                        Console.WriteLine(reader);
                        Console.WriteLine(reader[0] + ", " + reader[1] + ", " + reader[2] + ", " + reader[3]);
                    }   
                    Console.ReadKey();
                }
            }
        }
    }
    ```
2. Выполните сборку и запустите приложение.  

## <a name="see-also"></a>См. также:
- [Using Always Encrypted with the .NET Framework Data Provider for SQL Server (Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server)](encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)