---
title: Шаг 4. Устойчивое подключение к SQL с помощью ADO.NET | Документация Майкрософт
description: Описывает подключение реЦилиентли к SQL
ms.custom: ''
ms.date: 08/15/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: rothja
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: v-kaywon
ms.author: v-kaywon
ms.openlocfilehash: 62ec2eb775ef5fba76b402d1871afe6c87bcc606
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451800"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Шаг 4. Выполнение устойчивого подключения к SQL с помощью ADO.NET

![Download-DownArrow-Circled](../../ssdt/media/download.png)[Скачать ADO.NET](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

- Предыдущая статья:&nbsp;&nbsp;&nbsp;[Шаг 3. Эксперимент, подразумевающий подключение к SQL с помощью ADO.NET](step-3-connect-sql-ado-net.md)  

  
Этот раздел содержит пример кода C#, который демонстрирует логику повторных попыток. Логика повторных попыток обеспечивает надежность. Логика повторных попыток предназначена для корректной обработки временных ошибок или временных *сбоев* , которые обычно исчезают, если программа ожидает несколько секунд и повторит попытку.  
  
Ниже перечислены источники временных сбоев.  
  
- Короткий сбой сети, поддерживающей Интернет.  
- Облачная система может подгружать ресурсы в момент отправки запроса.  
  
  
Классы ADO.NET, которые используются для подключения к локальному серверу Microsoft SQL, также можно подключать к базе данных SQL Azure. Однако сами классы ADO.NET не могут обеспечить устойчивость и надежность, необходимые для использования в рабочей среде. Клиентская программа может столкнуться с временными сбоями, из которых она должна автоматически восстанавливаться и продолжаться.  
  
## <a name="step-1-identify-transient-errors"></a>Шаг 1. выявление временных ошибок  
  
Программа должна различать временные ошибки и постоянные ошибки. Временные ошибки — это условия ошибок, которые могут очищаться в течение короткого периода времени, например временные проблемы с сетью.  Пример постоянной ошибки может возникать, если программа содержит опечатку в имени целевой базы данных. в этом случае ошибка "не найдена такая база данных" будет сохранена, и в течение короткого периода времени она не сможет быть очищена.  
  
Список номеров ошибок, классифицированных как временные ошибки, доступен в [сообщениях об ошибках для клиентских приложений базы данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/) .  
  
## <a name="step-2-create-and-run-sample-application"></a>Шаг 2. Создание и запуск примера приложения  
  
В этом примере предполагается, что установлен .NET Framework 4.5.1 или более поздней версии.  Пример C# кода состоит из одного файла с именем Program.cs. Его код приведен в следующем разделе.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Шаг 2. a. запись и Компиляция примера кода  
  
Пример можно скомпилировать, выполнив следующие действия.  
  
1. В [бесплатной версии Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs)создайте новый проект на основе шаблона C# консольного приложения.  
    - Файл > Новый > Проект > установленные > шаблоны > Visual C# > Windows > классический рабочий стол > консольное приложение  
    - Назовите проект **RetryAdo2**.  
2. Откройте панель обозреватель решений.  
    - См. имя проекта.  
    - См. имя файла Program.cs.  
3. Откройте файл Program.cs.  
4. Полностью замените содержимое файла Program.cs кодом в следующем блоке кода.  
5. Откройте меню Сборка > сборка решение.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Шаг 2. b. копирование и вставка примера кода  
  
Вставьте этот код в файл **Program.CS** .  
  
Затем необходимо изменить строки для имени сервера, пароля и т. д. Эти строки можно найти в методе с именем **жетсклконнектионстрингбуилдер**.  
  
Примечание. строка подключения для имени сервера нацелена на базу данных SQL Azure, так как она включает в себя четыре префикса символов для **TCP:** . Но можно настроить строку сервера для подключения к Microsoft SQL Server.  
  
  
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
  
###  <a name="step-2c-run-the-program"></a>Шаг 2. c. Запуск программы  
  
  
Исполняемый файл **RetryAdo2. exe** не имеет параметров. Чтобы запустить exe:  
  
1. Откройте окно консоли, в котором был скомпилирован двоичный файл RetryAdo2. exe.  
2. Запустите RetryAdo2. exe без входных параметров.  
  
  
  
```  
database_firewall_rules_table   245575913  
filestream_tombstone_2073058421 2073058421  
filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Шаг 3. способы проверки логики повторных попыток  
  
Существует множество способов моделирования временной ошибки для проверки логики повторных попыток.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Шаг 3. a. исключение тестового исключения  
  
Пример кода включает:  
  
- Небольшой второй класс с именем **тестсклексцептион**со свойством **Number**.  
- `//throw new TestSqlException(4060);`, которые можно раскомментировать.  
  
Если раскомментировать инструкцию throw и выполнить повторную компиляцию, следующий запуск **RetryAdo2. exe** выводит примерно следующий результат.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Шаг 3. b. повторное тестирование с постоянной ошибкой  
  
Чтобы доказать, что код правильно обрабатывает постоянные ошибки, перезапустите предыдущий тест, за исключением того, что не использует номер реальной временной ошибки, такой как 4060. Вместо этого используйте серьезные номер 7654321. Программа должна рассматривать это как постоянную ошибку и выполнять обход повторных попыток.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Шаг 3. c. Отключение от сети  
  
1. Отключите клиентский компьютер от сети.  
    - Для настольного компьютера отключите сетевой кабель.  
    - Для переносного компьютера нажмите сочетание клавиш, чтобы отключить сетевой адаптер.  
2. Запустите RetryAdo2. exe и дождитесь, пока консоль отобразит первую временную ошибку, возможно, 11001.  
3. Повторно подключитесь к сети, пока RetryAdo2. exe продолжит работу.  
4. Следите за тем, чтобы отчет консоли был успешным при последующей повторной попытке.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Шаг 2. d. Временная опечатка в имени сервера  
  
1. Временно добавьте 40615 с другим номером ошибки в **трансиентеррорнумберс**и выполните повторную компиляцию.  
2. Установите точку останова в строке: `new QC.SqlConnectionStringBuilder()`.  
3. Используйте функцию " *изменить и продолжить* " для непреднамеренного написания имени сервера, несколько строк ниже.  
    - Позвольте программе выполнить и вернуться к точке останова.  
    - Возникает ошибка 40615.  
4. Исправьте опечатку.  
5. Позвольте программе успешно запуститься и завершить работу.  
6. Удалите 40615 и выполните повторную компиляцию.  
  
## <a name="next-steps"></a>Дальнейшие действия  
  
Чтобы ознакомиться с другими рекомендациями по проектированию и практиЦиес, посетите страницу [Подключение к базе данных SQL: ссылки, рекомендации и рекомендации по проектированию](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
