---
title: Приложения ASP.NET, использующие дескрипторы ожидания
description: Содержит пример, демонстрирующий, как выполнять несколько одновременных команд со страницы ASP.NET, используя дескрипторы ожидания для управления операцией при завершении всех команд.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: f588597a-49de-4206-8463-4ef377e112ff
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 0550b67d32d18aa9095b316816ebcbf3494cf195
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75250958"
---
# <a name="aspnet-applications-using-wait-handles"></a>Приложения ASP.NET, использующие дескрипторы ожидания

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Модели обратного вызова и опроса для обработки асинхронных операций полезны, если приложение обрабатывает только одну асинхронную операцию за раз. Модели ожидания обеспечивают более гибкий способ обработки нескольких асинхронных операций. Имеются две модели ожидания, называемые по именам методов <xref:System.Threading.WaitHandle>, используемых для их реализации: модель ожидания Wait (Any) и модель ожидания Wait (All).  
  
Для использования любой модели ожидания необходимо использовать свойство <xref:System.IAsyncResult.AsyncWaitHandle%2A> объекта <xref:System.IAsyncResult>, возвращаемого методами <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> или <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>. Для методов <xref:System.Threading.WaitHandle.WaitAny%2A> и <xref:System.Threading.WaitHandle.WaitAll%2A> требуется отправить объекты <xref:System.Threading.WaitHandle> в виде аргумента, сгруппированного в массив.  
  
Оба метода ожидания отслеживают асинхронные операции, ожидая завершения. Метод <xref:System.Threading.WaitHandle.WaitAny%2A> ожидает завершения или истечения времени ожидания какой-либо операции. Если известно, что конкретная операция завершена, можно обработать ее результаты, а затем ждать завершения следующей операции или истечения времени ожидания. Метод <xref:System.Threading.WaitHandle.WaitAll%2A> до продолжения работы ожидает завершения или истечения времени ожидания для всех процессов в массиве экземпляров <xref:System.Threading.WaitHandle>.  
  
Модели ожидания наиболее эффективны в тех случаях, когда необходимо выполнить несколько операций с одинаковой длиной на разных серверах или если сервер достаточно мощный для одновременной обработки всех запросов. В приведенных здесь примерах три запроса имитируют долгосрочные процессы, добавляя команды WAITFOR различной длины к несущественным запросам SELECT.  
  
## <a name="example-wait-any-model"></a>Пример Модель ожидания Wait (Any)  
В следующем примере показана модель ожидания Wait (Any). После запуска трех асинхронных процессов вызывается метод <xref:System.Threading.WaitHandle.WaitAny%2A> для ожидания завершения любого из процессов. По мере завершения каждого процесса вызывается метод <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> и считывается полученный объект <xref:Microsoft.Data.SqlClient.SqlDataReader>. На этом этапе реальное приложение, скорее всего, будет использовать <xref:Microsoft.Data.SqlClient.SqlDataReader> для заполнения части страницы. В этом простом примере время завершения процесса добавляется в текстовое поле, соответствующее процессу. Взятые вместе значения времени в текстовых полях иллюстрируют следующее: каждый раз по завершении процесса выполняется код.  
  
Для настройки этого примера создайте новый проект веб-узла ASP.NET. Поместите элемент управления <xref:System.Web.UI.WebControls.Button> и четыре элемента управления <xref:System.Web.UI.WebControls.TextBox> на странице (принимая имя по умолчанию для каждого элемента управления).  
  
Добавьте следующий код в класс формы, изменив при необходимости строку подключения для вашей среды.  
  
```csharp  
// Add the following using statements, if they are not already there.  
using System;  
using System.Data;  
using System.Configuration;  
using System.Web;  
using System.Web.Security;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.UI.WebControls.WebParts;  
using System.Web.UI.HtmlControls;  
using System.Threading;  
using Microsoft.Data.SqlClient;  
  
// Add this code to the page's class  
string GetConnectionString()  
     //  To avoid storing the connection string in your code,              
     //  you can retrieve it from a configuration file.   
     //  If you have not included "Asynchronous Processing=true"   
     //  in the connection string, the command will not be able  
     //  to execute asynchronously.  
{  
     return "Data Source=(local);Integrated Security=SSPI;" +  
          "Initial Catalog=AdventureWorks;" +  
          "Asynchronous Processing=true";  
}  
void Button1_Click(object sender, System.EventArgs e)  
{  
     //  In a real-world application, you might be connecting to   
     //   three different servers or databases. For the example,  
     //   we connect to only one.  
  
     SqlConnection connection1 =   
          new SqlConnection(GetConnectionString());  
     SqlConnection connection2 =   
          new SqlConnection(GetConnectionString());  
     SqlConnection connection3 =   
          new SqlConnection(GetConnectionString());  
     //  To keep the example simple, all three asynchronous   
     //  processes select a row from the same table. WAITFOR  
     //  commands are used to emulate long-running processes  
     //  that complete after different periods of time.  
  
     string commandText1 = "WAITFOR DELAY '0:0:01';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     string commandText2 = "WAITFOR DELAY '0:0:05';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     string commandText3 = "WAITFOR DELAY '0:0:10';" +   
          "SELECT * FROM Production.Product " +   
          "WHERE ProductNumber = 'BL-2036'";  
     try  
          //  For each process, open a connection and begin   
          //  execution. Use the IAsyncResult object returned by   
          //  BeginExecuteReader to add a WaitHandle for the   
          //  process to the array.  
     {  
          connection1.Open();  
          SqlCommand command1 =  
               new SqlCommand(commandText1, connection1);  
          IAsyncResult result1 = command1.BeginExecuteReader();  
          WaitHandle waitHandle1 = result1.AsyncWaitHandle;  
  
          connection2.Open();  
          SqlCommand command2 =  
               new SqlCommand(commandText2, connection2);  
          IAsyncResult result2 = command2.BeginExecuteReader();  
          WaitHandle waitHandle2 = result2.AsyncWaitHandle;  
  
          connection3.Open();  
          SqlCommand command3 =  
               new SqlCommand(commandText3, connection3);  
          IAsyncResult result3 = command3.BeginExecuteReader();  
          WaitHandle waitHandle3 = result3.AsyncWaitHandle;  
  
          WaitHandle[] waitHandles = {  
               waitHandle1, waitHandle2, waitHandle3  
          };  
  
          int index;  
          for (int countWaits = 0; countWaits <= 2; countWaits++)  
          {  
               //  WaitAny waits for any of the processes to   
               //  complete. The return value is either the index   
               //  of the array element whose process just   
               //  completed, or the WaitTimeout value.  
  
               index = WaitHandle.WaitAny(waitHandles,   
                    60000, false);  
               //  This example doesn't actually do anything with   
               //  the data returned by the processes, but the   
               //  code opens readers for each just to demonstrate       
               //  the concept.  
               //  Instead of using the returned data to fill the   
               //  controls on the page, the example adds the time  
               //  the process was completed to the corresponding  
               //  text box.  
  
               switch (index)  
               {  
                    case 0:  
                         SqlDataReader reader1;  
                         reader1 =   
                              command1.EndExecuteReader(result1);  
                         if (reader1.Read())  
                         {  
                           TextBox1.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader1.Close();  
                         break;  
                    case 1:  
                         SqlDataReader reader2;  
                         reader2 =   
                              command2.EndExecuteReader(result2);  
                         if (reader2.Read())  
                         {  
                           TextBox2.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader2.Close();  
                         break;  
                    case 2:  
                         SqlDataReader reader3;  
                         reader3 =   
                              command3.EndExecuteReader(result3);  
                         if (reader3.Read())  
                         {  
                           TextBox3.Text =   
                           "Completed " +  
                           System.DateTime.Now.ToLongTimeString();  
                         }  
                         reader3.Close();  
                         break;  
                    case WaitHandle.WaitTimeout:  
                         throw new Exception("Timeout");  
                         break;  
               }  
          }  
     }  
     catch (Exception ex)  
     {  
          TextBox4.Text = ex.ToString();  
     }  
     connection1.Close();  
     connection2.Close();  
     connection3.Close();  
}  
```  
  
## <a name="example-wait-all-model"></a>Пример Модель ожидания Wait (All)  
В следующем примере показана модель ожидания Wait (All). После запуска трех асинхронных процессов вызывается метод <xref:System.Threading.WaitHandle.WaitAll%2A> для ожидания завершения процессов или истечения времени их ожидания.  
  
Как и в примере модели ожидания Wait (Any), время завершения процесса добавляется в текстовое поле, соответствующее процессу. Как уже упоминалось выше, значения времени в текстовых полях иллюстрируют следующее: код, следующий за методом <xref:System.Threading.WaitHandle.WaitAny%2A>, выполняется только после завершения всех процессов.  
  
Для настройки этого примера создайте новый проект веб-узла ASP.NET. Поместите элемент управления <xref:System.Web.UI.WebControls.Button> и четыре элемента управления <xref:System.Web.UI.WebControls.TextBox> на странице (принимая имя по умолчанию для каждого элемента управления).  
  
Добавьте следующий код в класс формы, изменив при необходимости строку подключения для вашей среды.  
  
```csharp  
// Add the following using statements, if they are not already there.  
using System;  
using System.Data;  
using System.Configuration;  
using System.Web;  
using System.Web.Security;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.UI.WebControls.WebParts;  
using System.Web.UI.HtmlControls;  
using System.Threading;  
using Microsoft.Data.SqlClient;  
  
// Add this code to the page's class  
string GetConnectionString()  
    //  To avoid storing the connection string in your code,              
    //  you can retrieve it from a configuration file.   
    //  If you have not included "Asynchronous Processing=true"   
    //  in the connection string, the command will not be able  
    //  to execute asynchronously.  
{  
    return "Data Source=(local);Integrated Security=SSPI;" +  
        "Initial Catalog=AdventureWorks;" +  
        "Asynchronous Processing=true";  
}  
void Button1_Click(object sender, System.EventArgs e)  
{  
    //  In a real-world application, you might be connecting to   
    //   three different servers or databases. For the example,  
    //   we connect to only one.  
  
    SqlConnection connection1 =   
        new SqlConnection(GetConnectionString());  
    SqlConnection connection2 =   
        new SqlConnection(GetConnectionString());  
    SqlConnection connection3 =   
        new SqlConnection(GetConnectionString());  
    //  To keep the example simple, all three asynchronous   
    //  processes execute UPDATE queries that result in  
      //  no change to the data. WAITFOR  
    //  commands are used to emulate long-running processes  
    //  that complete after different periods of time.  
  
    string commandText1 =   
        "UPDATE Production.Product " +  
        "SET ReorderPoint = ReorderPoint + 1 " +  
        "WHERE ReorderPoint Is Not Null;" +  
        "WAITFOR DELAY '0:0:01';" +  
        "UPDATE Production.Product " +  
        "SET ReorderPoint = ReorderPoint - 1 " +  
        "WHERE ReorderPoint Is Not Null";  
  
    string commandText2 =   
      "UPDATE Production.Product " +  
      "SET ReorderPoint = ReorderPoint + 1 " +  
      "WHERE ReorderPoint Is Not Null;" +  
      "WAITFOR DELAY '0:0:05';" +  
      "UPDATE Production.Product " +  
      "SET ReorderPoint = ReorderPoint - 1 " +  
      "WHERE ReorderPoint Is Not Null";  
  
    string commandText3 =  
       "UPDATE Production.Product " +  
       "SET ReorderPoint = ReorderPoint + 1 " +  
       "WHERE ReorderPoint Is Not Null;" +  
       "WAITFOR DELAY '0:0:10';" +  
       "UPDATE Production.Product " +  
       "SET ReorderPoint = ReorderPoint - 1 " +  
       "WHERE ReorderPoint Is Not Null";  
    try  
        //  For each process, open a connection and begin   
        //  execution. Use the IAsyncResult object returned by   
        //  BeginExecuteReader to add a WaitHandle for the   
        //  process to the array.  
    {  
        connection1.Open();  
        SqlCommand command1 =  
            new SqlCommand(commandText1, connection1);  
        IAsyncResult result1 = command1.BeginExecuteNonQuery();  
        WaitHandle waitHandle1 = result1.AsyncWaitHandle;  
        connection2.Open();  
  
        SqlCommand command2 =  
            new SqlCommand(commandText2, connection2);  
        IAsyncResult result2 = command2.BeginExecuteNonQuery();  
        WaitHandle waitHandle2 = result2.AsyncWaitHandle;  
        connection3.Open();  
  
        SqlCommand command3 =  
            new SqlCommand(commandText3, connection3);  
        IAsyncResult result3 = command3.BeginExecuteNonQuery();  
        WaitHandle waitHandle3 = result3.AsyncWaitHandle;  
  
        WaitHandle[] waitHandles = {  
            waitHandle1, waitHandle2, waitHandle3  
        };  
  
        bool result;  
        //  WaitAll waits for all of the processes to   
        //  complete. The return value is True if the processes  
        //  all completed successfully, False if any process  
        //  timed out.  
  
        result = WaitHandle.WaitAll(waitHandles, 60000, false);  
        if(result)  
        {  
            long rowCount1 =   
                command1.EndExecuteNonQuery(result1);  
            TextBox1.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
            long rowCount2 =   
                command2.EndExecuteNonQuery(result2);  
            TextBox2.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
  
            long rowCount3 =   
                command3.EndExecuteNonQuery(result3);  
            TextBox3.Text = "Completed " +  
                System.DateTime.Now.ToLongTimeString();  
        }  
        else  
        {  
            throw new Exception("Timeout");  
        }  
    }  
  
    catch (Exception ex)  
    {  
        TextBox4.Text = ex.ToString();  
    }  
    connection1.Close();  
    connection2.Close();  
    connection3.Close();  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Асинхронные операции](asynchronous-operations.md)
