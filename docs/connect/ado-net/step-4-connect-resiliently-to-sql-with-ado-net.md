---
title: 'Шаг 4: Выполнение устойчивого подключения к SQL с помощью ADO.NET | Документация Майкрософт'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 483c7f84d171b34135d16fd6f392b6f5f180d217
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607104"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Шаг 4. Выполнение устойчивого подключения к SQL с помощью ADO.NET

- Предыдущая статья:&nbsp;&nbsp;&nbsp;[Шаг 3. Эксперимент, подразумевающий подключение к SQL с помощью ADO.NET](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
Этот раздел содержит пример кода C#, демонстрирующий пользовательскую логику повторных попыток. Логика повторных попыток обеспечивает надежность. Логика повторных попыток предназначена для корректной обработки временных ошибок или *временные сбои* который зачастую исчезают, если программа ожидает несколько секунд и повторит попытку.  
  
Источники временные сбои включают:  
  
- Brief: Сбой сетевого подключения, которая поддерживает Интернет.  
- Облачная система может быть балансировки ресурсов на данный момент отправки вашего запроса.  
  
  
Классы ADO.NET для подключения к локальному серверу Microsoft SQL можно также подключиться к базе данных SQL Azure. Тем не менее сами по себе ADO.NET классов не может предоставить все стабильность и надежность, необходимые в процессе эксплуатации. Клиентская программа может испытывать временные сбои, из которых он должен в автоматическом режиме и корректно восстановить и сам по себе.  
  
## <a name="step-1-identify-transient-errors"></a>Шаг 1: Определение временных ошибок  
  
Программа должна отличать временные ошибки от постоянных. Временные ошибки приведены неправильные условия, которые может очистить за короткий промежуток времени, например временные сетевые проблемы.  Пример устойчивая ошибка бы, если программа содержит опечатку в имени целевой базы данных — в этом случае ошибка «База данных не найден» сохранится и очистки в течение короткого периода времени не может.  
  
Список кодов ошибок, которые считаются временными сбоями доступен в [сообщения об ошибках для клиентских приложений базы данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Шаг 2: Создание и запуск примера приложения  
  
В этом примере предполагается, что .NET Framework 4.5.1 или более поздней.  В примере кода C# состоит из одного файла, с именем Program.cs. Его код приведен в следующем разделе.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Шаг 2.a: записи и компиляции примера кода  
  
Можно скомпилировать образец, выполнив следующие действия:  
  
1. В [бесплатный выпуск Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs), создайте новый проект на основе шаблона консольного приложения C#.  
    - Файл > Создать > проект > установлен > Шаблоны > Visual C# > Windows > классический рабочий стол > консольное приложение  
    - Назовите проект **RetryAdo2**.  
2. Откройте панель обозревателя решений.  
    - См. в разделе имя проекта.  
    - См. в разделе имя файла Program.cs.  
3. Откройте файл Program.cs.  
4. Полностью Замените содержимое файла Program.cs кодом из приведенного ниже кода.  
5. Выберите в меню сборка > построить решение.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Шаг 2.b: Копировать и вставить пример кода  
  
Вставьте этот код в вашей **Program.cs** файл.  
  
Затем необходимо изменить строки для имени сервера, пароль и т. д. Эти строки можно найти в методе с именем **GetSqlConnectionStringBuilder**.  
  
Примечание: Строка подключения для имени сервера ориентирована на базы данных SQL Azure, так как он включает четыре символа префикса **tcp:**. Но вы можете настроить строку подключения к серверу Microsoft SQL Server сервера.  
  
  
```CSharp  
    using System;  // C#  
    using CG = System.Collections.Generic;  
    using QC = System.Data.SqlClient;  
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
  
###  <a name="step-2c-run-the-program"></a>Шаг 2.c: запустите программу  
  
  
**RetryAdo2.exe** исполняемый файл не принимает никаких параметров. Для запуска .exe:  
  
1. Откройте окно консоли, для которых была выполнена компиляция двоичного файла RetryAdo2.exe.  
2. Выполнения RetryAdo2.exe без входных параметров.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Шаг 3: Способы тестирования логики повторных попыток  
  
Существует множество способов можно имитировать временных ошибок для тестирования логики повторных попыток.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Шаг 3а: исключение теста  
  
Пример кода включает:  
  
- Небольшой класс **TestSqlException**, со свойством, именуемым **номер**.  
- `//throw new TestSqlException(4060);` , которую можно раскомментировать.  
  
Если раскомментировать инструкции throw и повторите компиляцию, при следующем выполнении **RetryAdo2.exe** вывод будет примерно следующим.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Шаге 3.b: повторное тестирование с постоянными ошибками  
  
Чтобы убедиться, что код обработчиков, которые постоянных ошибок, повторно запустите предыдущий тест, но не используйте номер реальной временной ошибки, например, 4060. Вместо этого используйте любой другой номер 7654321. Программу следует считать это устойчивая ошибка и нужно пропустить все повторные попытки.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Шаг 3.c: отключить от сети  
  
1. Отключите клиентский компьютер от сети.  
    - Для настольных компьютеров отключите сетевой кабель.  
    - Случае с ноутбуком нажмите функциональное сочетание клавиш для отключения сетевого адаптера.  
2. Запустите RetryAdo2.exe и дождитесь в консоли отобразится первая временная ошибка, скорее всего, 11001.  
3. Повторно подключиться к сети, а RetryAdo2.exe продолжит выполняться.  
4. Просмотрите отчет консоли об успешном последующих повторных попыток.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Шаг 2.d: временно исказить имя сервера  
  
1. Временно добавьте 40615 в качестве другого номера ошибки **TransientErrorNumbers**и повторите компиляцию.  
2. Установите точку останова в строке: `new QC.SqlConnectionStringBuilder()`.  
3. Используйте *изменить и продолжить* чтобы специально исказить имя сервера, на несколько строк ниже.  
    - Позвольте запустите программу и вернитесь к точке останова.  
    - Возникает ошибка 40615.  
4. Исправьте ошибку в имени.  
5. Позвольте программе успешно завершенные.  
6. Удалите 40615 и повторите компиляцию.  
  
## <a name="next-steps"></a>Next Steps  
  
Чтобы изучить другие practicies рекомендации и советы по разработке, посетите [подключение к базе данных SQL: ссылки, рекомендации и советы по разработке](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
