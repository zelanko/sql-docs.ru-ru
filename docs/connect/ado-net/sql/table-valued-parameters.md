---
title: Возвращающие табличные значения параметры
description: Здесь описывается работа с возвращающими табличное значение параметрами, появившимися в SQL Server 2008.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 29c7be3fbcb027d1789357d0ce823ac6b1c59f2a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75243979"
---
# <a name="table-valued-parameters"></a>Возвращающие табличные значения параметры

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которой затем можно управлять с помощью Transact-SQL.  
  
Доступ к значениям столбца в возвращающих табличное значение параметрах обеспечивается с помощью стандартных инструкций Transact-SQL SELECT. Возвращающие табличное значение параметры строго типизированы, и проверка их структуры происходит автоматически. Размер возвращающих табличное значение параметров ограничен только объемом памяти сервера.  
  
> [!NOTE]
>  В параметре, возвращающем табличное значение, невозможно вернуть данные. Возвращающие табличное значение параметры являются только входными. Ключевое слово OUTPUT не поддерживается.  
  
Дополнительные сведения о возвращающих табличное значение параметрах см. в следующих ресурсах.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Возвращающие табличное значение параметры (ядро СУБД)](https://go.microsoft.com/fwlink/?LinkId=98363) в электронной документации на SQL Server|Здесь описывается создание и использование возвращающих табличное значение параметров.|  
|[Определяемые пользователем табличные типы](https://go.microsoft.com/fwlink/?LinkId=98364) в электронной документации на SQL Server|Описывает использование определяемых пользователем табличных типов для объявления возвращающих табличное значение параметров.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Передача нескольких строк в предыдущих версиях SQL Server  
До появления в SQL Server 2008 параметров, возвращающих табличное значение, были ограниченны возможности передачи нескольких строк данных в хранимую процедуру или параметризованную команду SQL. Разработчик может выбрать один из следующих вариантов передачи нескольких строк на сервер.  
  
- Использовать ряд отдельных параметров, чтобы представить значения в нескольких столбцах и строках данных. Объем данных, которые можно передать с помощью этого метода, ограничен количеством допустимых параметров. В процедурах SQL Server можно использовать не более 2100 параметров. Для сборки этих отдельных значений в табличную переменную или временную таблицу для обработки требуется логика на стороне сервера.  
  
- Объединить несколько значений данных в строки с разделителями или документы XML, а затем передать эти текстовые значения в процедуру или инструкцию. Для этого требуется, чтобы процедура или инструкция содержали логику, необходимую для проверки структур данных и разъединения значений.  
  
- Создать ряд отдельных инструкций SQL для изменений данных, затрагивающих несколько строк, например, созданных путем вызова метода `Update` объекта <xref:Microsoft.Data.SqlClient.SqlDataAdapter>. Изменения можно отправлять на сервер по отдельности или объединять в группы. Тем не менее даже при отправке в пакетах, содержащих несколько инструкций, каждая из них выполняется на сервере отдельно.  
  
- Использовать программу `bcp` или объект <xref:Microsoft.Data.SqlClient.SqlBulkCopy>, чтобы загрузить в таблицу множество строк данных. Хотя этот метод очень эффективен, он не поддерживает обработку на стороне сервера, если данные не загружены во временную таблицу или табличную переменную.  
  
## <a name="creating-table-valued-parameter-types"></a>Создание типов параметров, возвращающих табличное значение  
Возвращающие табличное значение параметры основаны на строго типизированных табличных структурах, заданных с помощью инструкций Transact-SQL CREATE TYPE. Перед использованием в клиентских приложениях возвращающих табличное значение параметров в SQL Server необходимо создать табличный тип и определить структуру. Дополнительные сведения о создании типов таблиц см. в разделе [Определяемые пользователем табличные типы](https://go.microsoft.com/fwlink/?LinkID=98364) электронной документации на SQL Server.  
  
Следующая инструкция создает табличный тип с именем CategoryTableType, состоящий из столбцов CategoryID и CategoryName:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
После создания табличного типа можно объявить возвращающие табличное значение параметры на основе этого типа. В приведенном ниже фрагменте кода Transact-SQL демонстрируется объявление возвращающего табличное значение параметра в определении хранимой процедуры. Обратите внимание, что для объявления возвращающего табличное значение параметра требуется ключевое слово READONLY.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Изменение данных с помощью возвращающих табличное значение параметров (Transact-SQL)  
Возвращающие табличное значение параметры можно использовать во влияющих на несколько строк изменениях данных на основе наборов, выполняя одну инструкцию. Например, можно выбрать в возвращающем табличное значение параметре все строки и вставить их в таблицу базы данных. Кроме того, можно создать инструкцию UPDATE, присоединив возвращающий табличное значение параметр к таблице, которую необходимо обновить.  
  
В приведенной ниже инструкции Transact-SQL UPDATE демонстрируется соединение возвращающего табличное значение параметра с таблицей Categories. При использовании возвращающего табличное значение параметра со значением JOIN в предложении FROM необходимо также присвоить ему псевдоним, как показано здесь, где параметр с табличным значением имеет псевдоним "ec":  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
В этом примере кода Transact-SQL демонстрируется выбор строк из возвращающего табличное значение параметра для выполнения инструкции INSERT в одной операции на основе набора данных.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Ограничения возвращающих табличное значение параметров  
Для возвращающих табличное значение параметров существует несколько ограничений.  
  
- Возвращающие табличное значение параметры нельзя передавать [определяемым пользователем функциям CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md).  
  
- Возвращающие табличное значение параметры могут индексироваться только для поддержки ограничений UNIQUE или PRIMARY KEY. SQL Server не ведет статистику возвращающих табличные значения параметров.  
  
- В коде Transact-SQL возвращающие табличное значение параметры предназначены только для чтения. Нельзя обновлять значения столбцов в строках возвращающего табличное значение параметра, а также вставлять или удалять строки. Чтобы изменить данные, передаваемые в хранимую процедуру или параметризованную инструкцию в возвращающем табличное значение параметре, необходимо вставить данные во временную таблицу или в табличную переменную.  
  
- Нельзя использовать инструкции ALTER TABLE для изменения структуры возвращающих табличное значение параметров.  
  
## <a name="configuring-a-sqlparameter-example"></a>Пример настройки объекта SqlParameter  
Поставщик <xref:Microsoft.Data.SqlClient> поддерживает заполнение возвращающих табличное значение параметров из объектов <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> или <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.Data.SqlClient.Server.SqlDataRecord>. Необходимо указать имя типа возвращающего табличное значение параметра с помощью свойства <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> объекта <xref:Microsoft.Data.SqlClient.SqlParameter>. `TypeName` должно совпадать с именем совместимого типа, ранее созданного на сервере. В приведенном ниже фрагменте кода демонстрируется, как настроить <xref:Microsoft.Data.SqlClient.SqlParameter> для вставки данных.  
 
В следующем примере переменная `addedCategories` содержит <xref:System.Data.DataTable>. Чтобы увидеть, как заполняется переменная, просмотрите примеры в следующем разделе: [Передача возвращающего табличное значение параметра в хранимую процедуру](#passing).

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```   
  
Также для передачи строк данных в возвращающий табличное значение параметр можно использовать любой производный от <xref:System.Data.Common.DbDataReader> объект, как показано в этом фрагменте.  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
## <a name="passing"></a> Передача возвращающего табличное значение параметра в хранимую процедуру  
В этом примере демонстрируется передача данных возвращающего табличное значение параметра в хранимую процедуру. Код извлекает добавленные строки в новый объект <xref:System.Data.DataTable> с помощью метода <xref:System.Data.DataTable.GetChanges%2A>. Затем код определяет <xref:Microsoft.Data.SqlClient.SqlCommand>, устанавливая для свойства <xref:Microsoft.Data.SqlClient.SqlCommand.CommandType%2A> значение <xref:System.Data.CommandType.StoredProcedure>. <xref:Microsoft.Data.SqlClient.SqlParameter> заполняется с помощью метода <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A>, а параметру <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> задано значение `Structured`. Затем <xref:Microsoft.Data.SqlClient.SqlCommand> выполняется с помощью метода <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Передача возвращающего табличное значение параметра в параметризованную инструкцию SQL  
 В следующем примере показано, как вставить данные в таблицу dbo.Categories с помощью инструкции INSERT с вложенным запросом SELECT, имеющим в качестве источника данных возвращающий табличное значение параметр. При передаче возвращающего табличное значение параметра в параметризованную инструкцию SQL необходимо указать имя типа этого параметра с помощью нового свойства <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> объекта <xref:Microsoft.Data.SqlClient.SqlParameter>. `TypeName` должно совпадать с именем совместимого типа, ранее созданного на сервере. Код в этом примере использует свойство `TypeName` для ссылки на структуру типа, определенную в dbo.CategoryTableType.  
  
> [!NOTE]
>  Если для столбца идентификаторов задается значение в возвращающем табличное значение параметре, необходимо выполнить инструкцию SET IDENTITY_INSERT для сеанса.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>Потоковая передача строк с помощью DataReader  
Также для передачи строк данных в возвращающий табличное значение параметр можно использовать любой производный от <xref:System.Data.Common.DbDataReader> объект. В следующем фрагменте кода демонстрируется получение данных из базы данных Oracle с помощью <xref:System.Data.OracleClient.OracleCommand> и <xref:System.Data.OracleClient.OracleDataReader>. Затем код настраивает <xref:Microsoft.Data.SqlClient.SqlCommand> для вызова хранимой процедуры с одним входным параметром. Свойство <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> объекта <xref:Microsoft.Data.SqlClient.SqlParameter> имеет значение `Structured`. <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> передает результирующий набор `OracleDataReader` в хранимую процедуру в виде возвращающего табличное значение параметра.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Операции с данными SQL Server в ADO.NET](sql-server-data-operations.md)
