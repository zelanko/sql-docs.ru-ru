---
title: Приложения Windows, использующие обратные вызовы
description: Содержит пример, демонстрирующий безопасное выполнение асинхронной команды с правильной обработкой взаимодействия с формой и ее содержимым из отдельного потока.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: af2873f80a48cab28c0604d9dd5c6f79a2796bbf
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918464"
---
# <a name="windows-applications-using-callbacks"></a>Приложения Windows, использующие обратные вызовы

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

В большинстве сценариев асинхронной обработки вы захотите начать работу с базой данных и продолжить выполнение других процессов, не дожидаясь завершения операции с базой данных. Однако, во многих сценариях после завершения операции базы данных требуется выполнение дополнительных действий. Например, в приложении Windows вам может потребоваться делегирование длительной операции в фоновый поток, одновременно позволяя потоку пользовательского интерфейса оставаться в рабочем процессе. Однако, когда работа с базой данных будет завершена, вы захотите использовать результаты для заполнения формы. Этот тип сценария наилучшим образом реализуется с помощью обратного вызова.  
  
Обратный вызов определяется путем указания делегата <xref:System.AsyncCallback> в методе <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> или <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>. Делегат вызывается после завершения операции. Можно передать делегату ссылку на сам <xref:Microsoft.Data.SqlClient.SqlCommand>, что упрощает доступ к объекту <xref:Microsoft.Data.SqlClient.SqlCommand> и вызов соответствующего метода `End` без использования глобальной переменной.  
  
## <a name="example"></a>Пример  
Следующее приложение Windows демонстрирует использование метода <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, выполняющего инструкцию Transact-SQL, которая включает в себя задержку в несколько секунд (эмуляция длительной команды).  
  
В этом примере демонстрируется ряд важных методов, включая вызов метода, который взаимодействует с формой из отдельного потока. Кроме того, этот пример демонстрирует, как блокировать пользователей от одновременного выполнения команды несколько раз, и как убедиться, что форма не закроется еще до вызова процедуры обратного вызова.  
  
Чтобы настроить этот пример, создайте новое приложение Windows. Поместите элемент управления <xref:System.Windows.Forms.Button> и два элемента управления <xref:System.Windows.Forms.Label> в форме (принимая имя по умолчанию для каждого элемента управления). Добавьте следующий код в класс формы, изменив при необходимости строку подключения для вашей среды.  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on   
// the form's design surface in Visual Studio), and then add   
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus   
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the   
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object   
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,              
    // you can retrieve it from a configuration file.   
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        "wait...");
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for   
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the   
            // SqlCommand object as the second parameter in the   
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus($"Ready (last error: {ex.Message})");
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that   
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.   
        DisplayInfoDelegate del =   
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,   
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't   
        // handle it here. You can either log the exception or   
        // invoke a delegate (as in the non-error case in this   
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a   
        // delegate as in the try block here.   
  
        // You can create the delegate instance as you   
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
            $"Ready (last error: {ex.Message}");
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Асинхронные операции](asynchronous-operations.md)
