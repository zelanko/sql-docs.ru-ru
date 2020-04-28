---
title: Извлечение данных определяемого пользователем типа | Документация Майкрософт
description: В этой статье описывается, как получить доступ к определяемым пользователем типам в базе данных SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d14c6d24d6db5d27b12bcc3f28c1b6ba383442
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488233"
---
# <a name="accessing-user-defined-types---retrieving-udt-data"></a>Доступ к определяемым пользователем типам — извлечение определяемых пользователем данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Чтобы создать на клиенте определяемый пользователем тип, сборка, зарегистрированная в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как определяемый пользователем тип, должна быть доступна для клиентского приложения. Сборку определяемого пользователем типа можно разместить в одном каталоге с приложением или в глобальном кэше сборок. Также можно задать ссылку на сборку в проекте.  
  
## <a name="requirements-for-using-udts-in-adonet"></a>Требования к использованию определяемых пользователем типов в ADO.NET  
 Чтобы создать на клиенте определяемый пользователем тип, сборка, загруженная в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и сборка на клиенте должны быть совместимы. Для определяемых пользователем типов, определенных в **собственном** формате сериализации, сборки должны быть совместимы с структурной совместимостью. Для сборок, определенных в формате **пользователяопределенные** , сборка должна быть доступна на клиенте.  
  
 Для получения необработанных данных из столбца определяемого пользователем типа таблицы копировать сборку определяемого пользователем типа на клиент не нужно.  
  
> [!NOTE]  
>  **SqlClient** может не загрузить определяемый пользователем тип в случае несовпадения версий ОПРЕДЕЛЯЕМОГО пользователем типа или других проблем. В этом случае для определения причин, по которым сборку, содержащую определяемый пользователем тип, нельзя использовать в вызывающем приложении, используйте обычные механизмы устранения неполадок. Дополнительные сведения см. в разделе «Диагностика ошибок с помощью управляемых помощников по отладке» документации по платформе .NET Framework.  
  
## <a name="accessing-udts-with-a-sqldatareader"></a>Доступ к определяемым пользователем типам с помощью объекта SqlDataReader  
 **System. Data. SqlClient. SqlDataReader** можно использовать из клиентского кода для получения результирующего набора, содержащего столбец определяемого пользователем типа, который предоставляется как экземпляр объекта.  
  
### <a name="example"></a>Пример  
 В этом примере показано, как использовать метод **Main** для создания нового объекта **SqlDataReader** . В этом примере кода выполняются следующие действия.  
  
1.  Метод Main создает новый объект **SqlDataReader** и получает значения из таблицы Points, которая имеет столбец определяемого пользователем типа с именем Point.  
  
2.  Определяемый пользователем тип Point представляет координаты X и Y, определенные как целые числа.  
  
3.  Определяемый пользователем тип определяет метод **расстояния** и метод **жетдистанцефромкси** .  
  
4.  Образец кода получает значения первичного ключа и столбцов определяемого пользователем типа, чтобы продемонстрировать его возможности.  
  
5.  Пример кода вызывает методы **Point. Distance** и **Point. жетдистанцефромкси** .  
  
6.  Результаты выводятся в окне консоли.  
  
> [!NOTE]  
>  Приложение должно содержать ссылку на сборку определяемого пользователем типа.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a>Привязка определяемых пользователем типов в виде байт  
 Иногда может потребоваться получить необработанные данные из столбца определяемого пользователем типа. Возможно, что тип недоступен локально, либо создание экземпляра определяемого пользователем типа нежелательно. Можно считать необработанные байты в массив байтов с помощью метода **GetBytes** объекта **SqlDataReader**. Этот метод считывает поток байт с указанного смещения столбца в буфер в виде массива, начиная с указанного смещения. Другим вариантом является использование одного из методов **жетсклбитес** или **жетсклбинари** и чтение всего содержимого в одной операции. В любом случае объект определяемого пользователем типа не создается, так что в клиентской сборке создание ссылки на определяемый пользователем тип не требуется.  
  
### <a name="example"></a>Пример  
 В этом примере показано, как получить данные **точки** как необработанные байты в массив байтов с помощью **SqlDataReader**. Код использует **System. Text. StringBuilder** для преобразования необработанных байтов в строковое представление, отображаемое в окне консоли.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a>Пример использования функции GetSqlBytes  
 В этом примере показано, как получить данные **точки** как необработанные байты в одной операции с помощью метода **жетсклбитес** . В коде используется класс **StringBuilder** для преобразования необработанных байтов в строковое представление, отображаемое в окне консоли.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a>Работа с параметрами определяемого пользователем типа  
 Определяемые пользователем типы используются в коде ADO.NET как в качестве входных, так и в качестве выходных параметров.  
  
## <a name="using-udts-in-query-parameters"></a>Использование определяемых пользователем типов в параметрах запроса  
 Определяемые пользователем типы могут использоваться в качестве значений параметров при настройке **SqlParameter** для объекта **System. Data. SqlClient. SqlCommand** . Перечисление **SqlDbType. UDT** объекта **SqlParameter** используется для указания на то, что параметр является определяемым пользователем типом при вызове метода **Add** в коллекцию **Parameters** . Свойство **UdtTypeName** объекта **SqlCommand** используется для указания полного имени определяемого пользователем типа в базе данных с помощью синтаксиса *Database. schema_name. object_name* . Несмотря на то, что использование полного имени не требуется, это удаляет неоднозначность из кода.  
  
> [!NOTE]  
>  Локальная копия сборки определяемого пользователем типа должна быть доступна в проекте клиента.  
  
### <a name="example"></a>Пример  
 Код в этом примере создает объекты **SqlCommand** и **SqlParameter** для вставки данных в столбец определяемого пользователем типа в таблице. В коде используется перечисление **SqlDbType. UDT** для указания типа данных, а свойство **UdtTypeName** объекта **SqlParameter** — для указания полного имени определяемого пользователем типа в базе данных.  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      
      param.UdtTypeName = "TestPoint.dbo.Point"      
      param.Direction = ParameterDirection.Input      
      param.Value = New Point(5, 6)      
      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Доступ к определяемым пользователем типам в ADO.NET](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
  
  
