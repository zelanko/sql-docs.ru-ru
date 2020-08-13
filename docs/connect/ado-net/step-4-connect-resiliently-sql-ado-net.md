---
title: Шаг 4. Выполнение устойчивого подключения к SQL с помощью ADO.NET
description: Сведения о том, как использовать логику повторных попыток для повышения устойчивости подключения к базе данных SQL с помощью ADO.NET.
ms.custom: ''
ms.date: 08/15/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: a70b5449d1af02c3b367a204e2e32dfb32281d72
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391769"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Шаг 4. Выполнение устойчивого подключения к SQL с помощью ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

- Предыдущая статья:&nbsp;&nbsp;&nbsp;[Step 3: Proof of concept connecting to SQL using ADO.NET](step-3-connect-sql-ado-net.md) (Шаг 3.Подтверждение концепции, подразумевающее подключение к SQL с помощью ADO.NET)  

  
Этот раздел содержит пример кода C#, который демонстрирует логику повторных попыток. Логика повторных попыток обеспечивает надежность. Логика повторных попыток предназначена для корректной обработки временных ошибок или *временных сбоев*, которые обычно устраняются, если программа ожидает несколько секунд, а затем выполняет повторную попытку.  
  
Ниже перечислены источники временных сбоев.  
  
- Кратковременный сбой в работе сети, поддерживающей Интернет.  
- Облачная система может балансировать нагрузку на свои ресурсы в момент отправки запроса.  
  
  
Классы ADO.NET, которые используются для подключения к локальному серверу Microsoft SQL, также можно подключать к базе данных SQL Azure. При этом сами по себе классы ADO.NET необходимый для работы уровень надежности обеспечить не могут. Ваша клиентская программа может испытывать временные сбои, с которыми она должна справляться самостоятельно, продолжая работу без вмешательства пользователя.  
  
## <a name="step-1-identify-transient-errors"></a>Шаг 1. Выявление временных ошибок  
  
Программа должна отличать временные ошибки от постоянных. Временные ошибки — это условия возникновения ошибок, которые можно устранить в течение короткого периода времени, например, временные проблемы с сетью.  Примером постоянной ошибки может быть случай, когда программа содержит опечатку в имени целевой базы данных. В этом случае ошибка "No such database found" (Такой базы данных не найдено) будет сохраняться, и не будет устранена в течение короткого времени.  
  
Список номеров ошибок, которые считаются временными сбоями, можно найти в статье [Troubleshooting connectivity issues and other errors with Microsoft Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/) (Устранение неполадок с соединениями и других ошибок с Базой данных SQL Microsoft Azure)  
  
## <a name="step-2-create-and-run-sample-application"></a>Шаг 2. Создание и запуск примера приложения  
  
В том примере предполагается, что установлена среда .NET Framework версии 4.5.1 или более поздней версии.  Пример кода C# состоит из одного файла с именем Program.cs. Этот код приведен в следующем разделе.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Шаг 2.а. Запись и компиляция примера кода  
  
Чтобы скомпилировать пример кода, выполните указанные ниже действия.  
  
1. В [бесплатном выпуске Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs)создайте новый проект на основе шаблона консольного приложения C#.  
    - Выберите Файл > Создать > Проект > Установленные> Шаблоны > Visual C# > Windows > Классический рабочий стол> Консольное приложение.  
    - Присвойте проекту имя **RetryAdo2**.  
2. Откройте панель обозревателя решений.  
    - Найдите имя своего проекта.  
    - Найдите имя файла Program.cs.  
3. Откройте файл Program.cs.  
4. Замените все содержимое файла Program.cs приведенным ниже кодом.  
5. Щелкните меню «Сборка» > «Собрать решение».  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Шаг 2.б. Копирование и вставка примера кода  
  
Вставьте этот код в ваш файл **Program.cs** .  
  
Затем необходимо изменить строки для имени сервера, пароля и т. д. Эти строки можно найти в методе с именем **GetSqlConnectionStringBuilder**.  
  
Примечание. Строка подключения для имени сервера нацелена на Базу данных SQL Azure, так как она включает в себя четыре префикса символов **tcp:** . Однако строку сервера можно настроить на подключение к Microsoft SQL Server.  
  
  
```csharp
using System;  // C#  
using CG = System.Collections.Generic;  
using QC = Microsoft.Data.SqlClient;  
using TD = System.Threading;  
    
namespace RetryAdo2  
{  
  public class Program  
  {  
    static public int Main(string[] args)  
    {  
      bool succeeded = false;  
      int totalNumberOfTimesToTry = 4;  
      int retryIntervalSeconds = 10;  
    
      for (int tries = 1;  
        tries <= totalNumberOfTimesToTry;  
        tries++)  
      {  
        try  
        {  
          if (tries > 1)  
          {  
            Console.WriteLine  
              ("Transient error encountered. Will begin attempt number {0} of {1} max...",  
              tries, totalNumberOfTimesToTry  
              );  
            TD.Thread.Sleep(1000 * retryIntervalSeconds);  
            retryIntervalSeconds = Convert.ToInt32  
              (retryIntervalSeconds * 1.5);  
          }  
          AccessDatabase();  
          succeeded = true;  
          break;  
        }  
    
        catch (QC.SqlException sqlExc)  
        {  
          if (TransientErrorNumbers.Contains  
            (sqlExc.Number) == true)  
          {  
            Console.WriteLine("{0}: transient occurred.", sqlExc.Number);  
            continue;  
          }  
          else  
          {  
            Console.WriteLine(sqlExc);  
            succeeded = false;  
            break;  
          }  
        }  
    
        catch (TestSqlException sqlExc)  
        {  
          if (TransientErrorNumbers.Contains  
            (sqlExc.Number) == true)  
          {  
            Console.WriteLine("{0}: transient occurred. (TESTING.)", sqlExc.Number);  
            continue;  
          }  
          else  
          {  
            Console.WriteLine(sqlExc);  
            succeeded = false;  
            break;  
          }  
        }  
    
        catch (Exception Exc)  
        {  
          Console.WriteLine(Exc);  
          succeeded = false;  
          break;  
        }  
      }  
    
      if (succeeded == true)  
      {  
        return 0;  
      }  
      else  
      {  
        Console.WriteLine("ERROR: Unable to access the database!");  
        return 1;  
      }  
    }  
    
    /// <summary>  
    /// Connects to the database, reads,  
    /// prints results to the console.  
    /// </summary>  
    static public void AccessDatabase()  
    {  
      //throw new TestSqlException(4060); //(7654321);  // Uncomment for testing.  
    
      using (var sqlConnection = new QC.SqlConnection  
          (GetSqlConnectionString()))  
      {  
        using (var dbCommand = sqlConnection.CreateCommand())  
        {  
          dbCommand.CommandText = @"  
SELECT TOP 3  
    ob.name,  
    CAST(ob.object_id as nvarchar(32)) as [object_id]  
  FROM sys.objects as ob  
  WHERE ob.type='IT'  
  ORDER BY ob.name;";  
    
          sqlConnection.Open();  
          var dataReader = dbCommand.ExecuteReader();  
    
          while (dataReader.Read())  
          {  
            Console.WriteLine("{0}\t{1}",  
              dataReader.GetString(0),  
              dataReader.GetString(1));  
          }  
        }  
      }  
    }  
    
    /// <summary>  
    /// You must edit the four 'my' string values.  
    /// </summary>  
    /// <returns>An ADO.NET connection string.</returns>  
    static private string GetSqlConnectionString()  
    {  
      // Prepare the connection string to Azure SQL Database.  
      var sqlConnectionSB = new QC.SqlConnectionStringBuilder();  
    
      // Change these values to your values.  
      sqlConnectionSB.DataSource = "tcp:myazuresqldbserver.database.windows.net,1433"; //["Server"]  
      sqlConnectionSB.InitialCatalog = "MyDatabase"; //["Database"]  
    
      sqlConnectionSB.UserID = "MyLogin";  // "@yourservername"  as suffix sometimes.  
      sqlConnectionSB.Password = "MyPassword";  
      sqlConnectionSB.IntegratedSecurity = false;  
    
      // Adjust these values if you like. (ADO.NET 4.5.1 or later.)  
      sqlConnectionSB.ConnectRetryCount = 3;  
      sqlConnectionSB.ConnectRetryInterval = 10;  // Seconds.  
    
      // Leave these values as they are.  
      sqlConnectionSB.IntegratedSecurity = false;  
      sqlConnectionSB.Encrypt = true;  
      sqlConnectionSB.ConnectTimeout = 30;  
    
      return sqlConnectionSB.ToString();  
    }  
    
    static public CG.List<int> TransientErrorNumbers =  
      new CG.List<int> { 4060, 40197, 40501, 40613,  
      49918, 49919, 49920, 11001 };  
  }  
    
  /// <summary>  
  /// For testing retry logic, you can have method  
  /// AccessDatabase start by throwing a new  
  /// TestSqlException with a Number that does  
  /// or does not match a transient error number  
  /// present in TransientErrorNumbers.  
  /// </summary>  
  internal class TestSqlException : ApplicationException  
  {  
    internal TestSqlException(int testErrorNumber)  
    { this.Number = testErrorNumber; }  
    
    internal int Number  
    { get; set; }  
  }  
}  
```  
  
###  <a name="step-2c-run-the-program"></a>Шаг 2.в. Запуск программы  
  
  
Исполняемый файл **RetryAdo2.exe** не принимает никаких параметров. Чтобы запустить ЕХЕ-файл:  
  
1. откройте окно консоли — там, где была выполнена компиляция двоичного файла RetryAdo2.exe;  
2. запустите файл RetryAdo2.exe без входных параметров.  
  
  
  
```  
database_firewall_rules_table   245575913  
filestream_tombstone_2073058421 2073058421  
filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Шаг 3. Способы тестирования логики повторных попыток  
  
Есть много разных способов имитации временных ошибок для тестирования логики повторных попыток.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Шаг 3.а. Вывод тестового исключения  
  
Пример кода включает:  
  
- небольшой второй класс с именем **TestSqlException** и свойством **Number**;  
- `//throw new TestSqlException(4060);` , которую можно раскомментировать.  
  
Если раскомментировать оператор throw и затем выполнить повторную компиляцию, при следующем выполнении файла **RetryAdo2.exe** вывод будет примерно следующим.  
  
```  
[C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
>> RetryAdo2.exe  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 2 of 4 max...  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 3 of 4 max...  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 4 of 4 max...  
4060: transient occurred. (TESTING.)  
ERROR: Unable to access the database!  
  
[C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
>>  
```  
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Шаг 3.б. Повторное тестирование с постоянными ошибками  
  
Чтобы убедиться, что код корректно обрабатывает постоянные ошибки, повторно выполните предыдущий тест, но не используйте номер реальной временной ошибки (например, 4060). Вместо этого используйте любой другой номер (например, 7654321). Программа должна обработать этот номер как номер постоянной ошибки, пропуская все повторные попытки.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Шаг 3.в. Отключение от сети  
  
1. Отключите клиентский компьютер от сети.  
    - В случае с настольным компьютером отключите сетевой кабель.  
    - В случае с ноутбуком нажмите функциональное сочетание клавиш для отключения сетевого адаптера.  
2. Запустите файл RetryAdo2.exe и дождитесь, пока в консоли отобразится первая временная ошибка (скорее всего, 11001).  
3. В ходе выполнения файла RetryAdo2.exe повторно подключитесь к сети.  
4. Просмотрите отчет консоли об успешном выполнении последующих повторных попыток.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Шаг 2.г. Временная опечатка в имени сервера  
  
1. Временно добавьте 40615 в поле **TransientErrorNumbers**в качестве другого номера ошибки, а затем выполните повторную компиляцию.  
2. Задайте точку останова строке: `new QC.SqlConnectionStringBuilder()`.  
3. Используйте параметр *Изменить и продолжить*, чтобы специально исказить имя сервера несколькими строками ниже.  
    - Запустите программу и вернитесь к точке останова.  
    - Произойдет ошибка 40615.  
4. Исправьте ошибку в имени.  
5. Запустите программу и дождитесь успешного завершения процедуры.  
6. Удалите 40615 и выполните повторную компиляцию.  
  
## <a name="next-steps"></a>Дальнейшие действия  
  
Чтобы изучить другие лучшие методики и рекомендации по разработке, перейдите на [Подключение к базе данных SQL: ссылки, рекомендации и советы по разработке](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
