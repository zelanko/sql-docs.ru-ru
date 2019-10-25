---
title: Статистика поставщика для SQL Server
description: Описание поддержки получения статистики времени выполнения SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 092cf63e62bce01e2a771ce4e5f7f46e1073e91a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452062"
---
# <a name="provider-statistics-for-sql-server"></a>Статистика поставщика для SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Начиная с версии .NET Framework 2,0 и .NET Core 1,0, поставщик данных Microsoft SqlClient для SQL Server поддерживает статистику времени выполнения. Необходимо включить статистику, задав для свойства <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> объекта <xref:Microsoft.Data.SqlClient.SqlConnection> значение `True` после создания допустимого объекта соединения. После включения статистики их можно просмотреть как "моментальный снимок во времени", извлекая <xref:System.Collections.IDictionary> ссылку с помощью метода <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> объекта <xref:Microsoft.Data.SqlClient.SqlConnection>. Перечислите список в виде набора пар "имя-значение" в словаре. Эти пары "имя-значение" не упорядочены. В любой момент можно вызвать метод <xref:Microsoft.Data.SqlClient.SqlConnection.ResetStatistics%2A> объекта <xref:Microsoft.Data.SqlClient.SqlConnection>, чтобы сбросить счетчики. Если сбор статистики не включен, исключение не создается. Кроме того, если <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> вызывается без вызова <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> First, то полученные значения являются начальными значениями для каждой записи. Если включить статистику, запустить приложение на некоторое время, а затем отключить статистику, полученные значения будут отражать значения, собранные до момента отключения статистики. Все собранные статистические значения приводятся отдельно для каждого подключения.  
  
## <a name="statistical-values-available"></a>Статистические значения доступны  
В настоящее время поставщику Microsoft SQL Server доступны 18 различных элементов. Доступ ко множеству элементов производится через свойство **Count** ссылки интерфейса <xref:System.Collections.IDictionary>, возвращенной <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Для всех счетчиков статистики поставщика используется тип среды CLR <xref:System.Int64> (**long** в C# и Visual Basic) с внутренним представлением длиной 64 бита. Максимальное значение типа данных **int64**, определенное полем **int64.MaxValue**, равно ((2^63)-1)). Если значения счетчиков достигли этого максимального значения, они больше не должны считаться точными. Это означает, что **int64.MaxValue**-1((2^63)-2) по существу является максимальным действительным значением любого статистического показателя.  
  
> [!NOTE]
>  Словарь используется для возврата статистики поставщика, так как число, имена и порядок возвращаемой статистики могут измениться в будущем. Приложения не должны полагаться на определенное значение в словаре, но вместо этого следует проверять, есть ли в нем значение, и выполнять ветвление соответствующим образом.  
  
В следующей таблице описаны доступные текущие статистические значения. Обратите внимание, что имена ключей для отдельных значений не локализованы в региональных версиях Microsoft .NET Framework и .NET Core.  
  
|Имя ключа|Описание|  
|--------------|-----------------|  
|`BuffersReceived`|Возвращает число пакетов потока табличных данных (TDS), полученных поставщиком из SQL Server после начала использования приложением поставщика и включения статистики.|  
|`BuffersSent`|Возвращает число пакетов TDS, отправленных поставщику SQL Server после включения статистики. Для больших команд может потребоваться несколько буферов. Например, если на сервер отправляется большая команда и требуется шесть пакетов, `ServerRoundtrips` увеличивается на единицу, `BuffersSent` увеличивается на шесть.|  
|`BytesReceived`|Возвращает число байтов данных в пакетах TDS, полученных поставщиком от SQL Server после начала использования приложением поставщика и включения статистики.|  
|`BytesSent`|Возвращает число байтов данных, отправленных SQL Server в пакетах TDS после начала использования приложением поставщика и включения статистики.|  
|`ConnectionTime`|Время в миллисекундах, в течение которого было открыто соединение после включения статистики (или полное время соединения, если статистика была включена до открытия соединения).|  
|`CursorOpens`|Возвращает число открытий курсора через соединение после начала использования приложением поставщика и включения статистики.<br /><br /> Обратите внимание, что результаты только для чтения и перенаправления, возвращаемые инструкциями SELECT, не считаются курсорами и поэтому не влияют на этот счетчик.|  
|`ExecutionTime`|Возвращает совокупное количество времени в миллисекундах, которое поставщик потратил на обработку после включения статистики, с учетом того времени, которое потрачено на ожидание ответов от сервера, а также времени, потраченного на выполнение кода самим поставщиком.<br /><br /> К классам, включающим код времени, относятся:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> склкоммандбуилдер<br /><br /> Чтобы элементы, критические для производительности, были максимально мелкими, следующие члены не имеют времени:<br /><br /> SqlDataReader<br /><br /> оператор [] (все перегрузки)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Возвращает общее число инструкций INSERT, DELETE и UPDATE, выполненных через соединение после начала использования приложением поставщика и включения статистики.|  
|`IduRows`|Возвращает общее число строк, затронутых инструкциями INSERT, DELETE и UPDATE, которые выполнялись через соединение после начала использования приложением поставщика и включения статистики.|  
|`NetworkServerTime`|Возвращает совокупное количество времени в миллисекундах, которое поставщик потратил на ожидание ответов от сервера после начала использования приложением поставщика и включения статистики.|  
|`PreparedExecs`|Возвращает число подготовленных команд, выполненных через соединение после начала использования приложением поставщика и включения статистики.|  
|`Prepares`|Возвращает число инструкций, подготовленных через соединение после начала использования приложением поставщика и включения статистики.|  
|`SelectCount`|Возвращает число инструкций SELECT, выполненных через соединение после начала использования приложением поставщика и включения статистики. Сюда входят инструкции FETCH для получения строк из курсоров, а счетчик для инструкций SELECT обновляется по достижении конца <xref:Microsoft.Data.SqlClient.SqlDataReader>.|  
|`SelectRows`|Возвращает число строк, выбранных после начала использования приложением поставщика и включения статистики. Этот счетчик отражает все строки, формируемые инструкциями SQL, даже те, которые не использовались вызывающим объектом фактически. Например, закрытие модуля чтения данных до считывания всего результирующего набора не повлияет на число. Сюда входят строки, полученные из курсоров с помощью инструкций FETCH.|  
|`ServerRoundtrips`|Возвращает количество попыток соединения отправить команды серверу и получил ответ обратно, когда приложение запустило использование поставщика и включил статистику.|  
|`SumResultSets`|Возвращает количество результирующих наборов, которые использовались после начала использования приложением поставщика и включения статистики. Например, это может быть любой результирующий набор, возвращаемый клиенту. Для курсоров каждая операция выборки или блокировки считается независимым результирующим набором.|  
|`Transactions`|Возвращает число пользовательских транзакций, запущенных после начала использования приложением поставщика и включения статистики, включая откаты. Если соединение работает с автоматической фиксацией, каждая команда считается транзакцией.<br /><br /> Этот счетчик увеличивает число транзакций, как только выполняется инструкция BEGIN TRAN, независимо от того, была ли транзакция зафиксирована или отменена позже.|  
|`UnpreparedExecs`|Возвращает число неподготовленных инструкций, выполненных через соединение после начала использования приложением поставщика и включения статистики.|  
  
### <a name="retrieving-a-value"></a>Получение значения  
В следующем консольном приложении показано, как включить статистику для соединения, получить четыре отдельных статистических значения и записать их в окно консоли.  
  
> [!NOTE]
>  В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server. В строке подключения, представленной в образце кода, предполагается, что база данных установлена и доступна на локальном компьютере. При необходимости измените строку подключения для вашей среды.  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Получение всех значений  
В следующем консольном приложении показано, как включить статистику для соединения, получить все доступные статистические значения с помощью перечислителя и записать их в окно консоли.  
  
> [!NOTE]
>  В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server. В строке подключения, представленной в образце кода, предполагается, что база данных установлена и доступна на локальном компьютере. При необходимости измените строку подключения для вашей среды.  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
