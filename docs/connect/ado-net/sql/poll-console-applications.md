---
title: Выполнение опросов в консольных приложениях
description: Содержит пример, демонстрирующий использование опроса для ожидания завершения выполнения асинхронной команды из консольного приложения. Этот метод также допустимый в библиотеке классов или другом приложении без пользовательского интерфейса.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 4ff084d5-5956-4db1-8e18-c5a66b000882
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 89bcaa6d6e92ccde2d1c151b493c26fe1279d89f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896646"
---
# <a name="polling-in-console-applications"></a>Выполнение опросов в консольных приложениях

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Асинхронные операции в ADO.NET позволяют инициировать длительные операции с базами данных в одном потоке, одновременно выполняя другие задачи в другом. Однако в большинстве сценариев, в конечном счете, вы достигнете точки, при которой вам нужно будет остановить работу приложения до завершения операции с базой данных. В таких случаях полезно выполнить опрос асинхронной операции, чтобы определить, завершена ли операция.  
  
Чтобы узнать, завершилась ли операция, можно использовать свойство <xref:System.IAsyncResult.IsCompleted%2A>.  
  
## <a name="example"></a>Пример  
В следующем приложении командной строки происходит асинхронное обновление данных в образце базы данных **AdventureWorks**. Чтобы эмулировать длительный процесс, в этом примере в текст команды вставляется инструкция WAITFOR. Обычно вам не нужно пытаться сделать выполнение команд медленнее, но в этом случае это упрощает демонстрацию асинхронного поведения.  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
    [STAThread]  
    static void Main()  
    {  
        // The WAITFOR statement simply adds enough time to   
        // prove the asynchronous nature of the command.  
  
        string commandText =  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint + 1 " +  
          "WHERE ReorderPoint Is Not Null;" +  
          "WAITFOR DELAY '0:0:3';" +  
          "UPDATE Production.Product SET ReorderPoint = " +  
          "ReorderPoint - 1 " +  
          "WHERE ReorderPoint Is Not Null";  
  
        RunCommandAsynchronously(  
            commandText, GetConnectionString());  
  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  
    private static void RunCommandAsynchronously(  
      string commandText, string connectionString)  
    {  
        // Given command text and connection string, asynchronously  
        // execute the specified command against the connection.   
        // For this example, the code displays an indicator as it's   
        // working, verifying the asynchronous behavior.   
        using (SqlConnection connection =  
          new SqlConnection(connectionString))  
        {  
            try  
            {  
                int count = 0;  
                SqlCommand command =   
                    new SqlCommand(commandText, connection);  
                connection.Open();  
  
                IAsyncResult result =   
                    command.BeginExecuteNonQuery();  
                while (!result.IsCompleted)  
                {  
                    Console.WriteLine(  
                                    "Waiting ({0})", count++);  
                    // Wait for 1/10 second, so the counter  
                    // doesn't consume all available   
                    // resources on the main thread.  
                    System.Threading.Thread.Sleep(100);  
                }  
                Console.WriteLine(  
                    "Command complete. Affected {0} rows.",  
                command.EndExecuteNonQuery(result));  
            }  
            catch (SqlException ex)  
            {  
                Console.WriteLine("Error ({0}): {1}",   
                    ex.Number, ex.Message);  
            }  
            catch (InvalidOperationException ex)  
            {  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
            catch (Exception ex)  
            {  
                // You might want to pass these errors  
                // back out to the caller.  
                Console.WriteLine("Error: {0}", ex.Message);  
            }  
        }  
    }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
  
        // If you have not included "Asynchronous Processing=true"  
        // in the connection string, the command will not be able  
        // to execute asynchronously.  
        return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks; " +   
        "Asynchronous Processing=true";  
    }  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Асинхронные операции](asynchronous-operations.md)
