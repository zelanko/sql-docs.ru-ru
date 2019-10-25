---
title: Манипулирование данными
description: Содержит примеры программирования приложений MARS.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: df430bbacb69e1d95d001e4f9340ca60473503cd
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452164"
---
# <a name="manipulating-data"></a>Манипулирование данными

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Перед введением нескольких активных результирующих наборов (MARS) разработчикам приходилось использовать несколько подключений или курсоры на стороне сервера для решения определенных сценариев. Кроме того, при использовании нескольких соединений в условиях транзакции приходилось прибегать к связанным соединениям (на основе системных хранимых процедур **sp_getbindtoken** и **sp_bindsession**). В следующих сценариях показано, как использовать подключение с включенным режимом MARS вместо нескольких подключений.  
  
## <a name="using-multiple-commands-with-mars"></a>Использование нескольких команд с режимом MARS  
В следующем консольном приложении показано, как использовать два <xref:Microsoft.Data.SqlClient.SqlDataReader> объектов с двумя <xref:Microsoft.Data.SqlClient.SqlCommand>ными объектами и один объект <xref:Microsoft.Data.SqlClient.SqlConnection> с включенным режимом MARS.  
  
### <a name="example"></a>Пример  
В этом примере открывается одно соединение с базой данных **AdventureWorks** . С помощью объекта <xref:Microsoft.Data.SqlClient.SqlCommand> создается <xref:Microsoft.Data.SqlClient.SqlDataReader>. По мере использования модуля чтения открывается вторая <xref:Microsoft.Data.SqlClient.SqlDataReader>, которая использует данные из первой <xref:Microsoft.Data.SqlClient.SqlDataReader> в качестве входных данных для второго средства чтения.  
  
> [!NOTE]
>  В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server. В строке подключения, представленной в образце кода, предполагается, что база данных установлена и доступна на локальном компьютере. При необходимости измените строку подключения для вашей среды.  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a>Чтение и обновление данных с помощью режима MARS  
Режим MARS позволяет использовать соединение как для операций чтения, так и для операций языка обработки данных (DML) с более чем одной ожидающей операцией. Эта функция устраняет необходимость в работе приложения с ошибками, занятыми соединением. Кроме того, режим MARS может заменить пользователя курсоров на стороне сервера, которые обычно потребляют больше ресурсов. Наконец, несколько операций могут осуществляться одновременно в одном соединении, поэтому в них может совместно использоваться один и тот же контекст транзакции, в результате чего отпадает необходимость использования системных хранимых процедур **sp_getbindtoken** и **sp_bindsession**.  
  
### <a name="example"></a>Пример  
В следующем консольном приложении показано, как использовать два <xref:Microsoft.Data.SqlClient.SqlDataReader> объектов с тремя <xref:Microsoft.Data.SqlClient.SqlCommand> объектами и один объект <xref:Microsoft.Data.SqlClient.SqlConnection> с включенным режимом MARS. Первый объект команды извлекает список поставщиков, чьи кредитные оценки — 5. Второй объект команды использует идентификатор поставщика, предоставленный из <xref:Microsoft.Data.SqlClient.SqlDataReader>, для загрузки второго <xref:Microsoft.Data.SqlClient.SqlDataReader> со всеми продуктами для конкретного поставщика. Каждая запись продукта посещается вторым <xref:Microsoft.Data.SqlClient.SqlDataReader>. Для определения нового состояния **OnOrderQty** выполняется вычисление. Затем используется третий объект команды для занесения в таблицу **ProductVendor** нового значения. Весь процесс выполняется в рамках одной транзакции, которая откатывается в конце.  
  
> [!NOTE]
>  В следующем примере используется образец базы данных **AdventureWorks**, входящий в состав SQL Server. В строке подключения, представленной в образце кода, предполагается, что база данных установлена и доступна на локальном компьютере. При необходимости измените строку подключения для вашей среды.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="next-steps"></a>Следующие шаги
- [Режим MARS](multiple-active-result-sets-mars.md)
