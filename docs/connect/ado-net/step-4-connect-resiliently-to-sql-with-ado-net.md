---
title: 'Шаг 4: Выполнение устойчивого подключения к SQL с помощью ADO.NET | Документы Microsoft'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: ado-net
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4c95f481bdd001ff85a63db9ebcc1c4438008447
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Шаг 4: Выполнение устойчивого подключения к SQL с помощью ADO.NET

- Предыдущей статьи:&nbsp;&nbsp;&nbsp;[Step 3: пробной версии при подключении к серверу SQL с помощью ADO.NET](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
Этот раздел содержит пример кода C#, демонстрирующий логику повторных попыток. Логика повторных попыток обеспечивает надежность. Логика повторов предназначена для верной обработки временных ошибок или *временные сбои* которой зачастую исчезают, если программа ожидает несколько секунд и повторных попыток.  
  
Временные сбои могут быть:  
  
- Краткое сбоя сети, которая поддерживает Интернета.  
- Облачная система может быть балансировки ресурсов в данный момент, которым выполняется запрос отправки.  
  
  
Классы ADO.NET для подключения к локальному серверу Microsoft SQL можно также подключиться к базе данных SQL Azure. Однако сами по себе ADO.NET классов не может предоставить все устойчивости и надежности, необходимым в процессе производственного использования. Временные сбои, из которых он должен в автоматическом режиме и правильно восстановить и продолжить сам по себе могут столкнуться с клиентской программе.  
  
## <a name="step-1-identify-transient-errors"></a>Шаг 1: Определение временных ошибок  
  
Программе необходимо отличать временных ошибок и вызваны ошибками. Временные сбои — это ошибки, которые могут очистить через небольшой промежуток времени, например временными неполадками сети.  Постоянные ошибки бы, если программа имеет ошибочное имя целевой базы данных — в этом случае сохранится ошибку «Такой база данных не найдено» и очистки в течение короткого периода времени не может.  
  
Список номеров ошибок, которые классифицируются как временные сбои в доступен в [сообщения об ошибках для клиентских приложений баз данных SQL](http://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Шаг 2: Создание и запустить образец приложения  
  
В этом примере предполагается, .NET Framework 4.5.1 или более поздней.  Пример кода C# состоит из одного файла Program.cs. Его код приведен в следующем разделе.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Шаг 2.a: записи и Скомпилируйте образец кода  
  
Можно скомпилировать образец с помощью следующих действий:  
  
1. В [бесплатный выпуск Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs), создайте новый проект на основе шаблона консольного приложения C#.  
    - Файл > Создать > проекта > установлен > Шаблоны > Visual C# > Windows > классического > консольное приложение  
    - Назовите проект **RetryAdo2**.  
2. Откройте панель обозревателя решений.  
    - Имя проекта отображается.  
    - Отображается имя файла Program.cs.  
3. Откройте файл Program.cs.  
4. Замените содержимое файла Program.cs кодом в следующем блоке кода полностью.  
5. Выберите в меню Построение > построить решение.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Шаг 2.b: Копировать и вставить пример кода  
  
Вставьте этот код в вашей **Program.cs** файла.  
  
Затем необходимо отредактировать строки для имени сервера, пароль и т. д. Эти строки можно найти в методе с именем **GetSqlConnectionStringBuilder**.  
  
Примечание: Строка подключения для имени сервера ориентирована базы данных SQL Azure, поскольку он включает четыре символа префикса **tcp:**. Однако можно скорректировать строка сервера для подключения к экземпляру Microsoft SQL Server.  
  
  
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
  
  
**RetryAdo2.exe** исполняемый файл входных данных без параметров. Запуск .exe:  
  
1. Откройте окно консоли, для которых был скомпилирован RetryAdo2.exe двоичный файл.  
2. Запустите RetryAdo2.exe, без входных параметров.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Шаг 3: Проверьте логику повторов способы  
  
Существует множество способов можно имитировать временная ошибка для тестирования логики повторных попыток.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Шаг 3.a: исключения теста  
  
Пример кода включает:  
  
- Небольшой класс **TestSqlException**, что свойство с именем **номер**.  
- `//throw new TestSqlException(4060);`, который вы можете раскомментировать.  
  
Если раскомментировать инструкции throw и перекомпилировать следующего запуска из **RetryAdo2.exe** выводит нечто похожее на следующее.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Шаг 3.b: повторное тестирование с устойчивая ошибка  
  
Для подтверждения кода обработчиков, которые вызваны ошибками правильно, повторно запустите предыдущем тесте, за исключением того, не используйте номер real временная ошибка как 4060. Вместо этого используйте номер не имеет смысла 7654321. Программа должна помечено как устойчивая ошибка и должен обходить любой повторных попыток.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Шаг 3.c: отключить от сети  
  
1. Отключите клиентский компьютер от сети.  
    - Для рабочего стола отключите сетевой кабель.  
    - Портативный компьютер нажмите клавишу функции сочетание клавиш для отключения сетевого адаптера.  
2. Запустите RetryAdo2.exe и дождитесь консоли для отображения первого временная ошибка, возможно, 11001.  
3. Подключитесь к сети, пока RetryAdo2.exe продолжает работать.  
4. Просмотрите отчет об успешном консоли на последующей повторной попыткой.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Шаг 2-г: временно написания имени сервера  
  
1. Временно добавить в качестве другой номер ошибки для 40615 **TransientErrorNumbers**и повторите компиляцию.  
2. Установите точку останова на строке: `new QC.SqlConnectionStringBuilder()`.  
3. Используйте *изменить и продолжить* возможность специально написания имени сервера, на несколько строк ниже.  
    - Позвольте программе запуска и вернуться к точке останова.  
    - 40615 произошла ошибка.  
4. Исправьте неправильное.  
5. Позвольте программе запуска и успешно завершена.  
6. Удалить 40615 и повторите компиляцию.  
  
## <a name="next-steps"></a>Следующие шаги  
  
Чтобы изучить другие practicies советы и рекомендации по проектированию, посетите [подключение к базе данных SQL: ссылки, рекомендации и рекомендации по проектированию](http://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
