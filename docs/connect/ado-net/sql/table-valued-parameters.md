---
title: Возвращающие табличные значения параметры
description: Описывает, как работать с возвращающими табличные значения параметрами, которые появились в SQL Server 2008.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: cb8eec87d0d36eb7deb8663e40407c0067967def
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451919"
---
# <a name="table-valued-parameters"></a>Возвращающие табличные значения параметры

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которой затем можно управлять с помощью Transact-SQL.  
  
Доступ к значениям столбца в возвращающих табличное значение параметрах обеспечивается с помощью стандартных инструкций Transact-SQL SELECT. Возвращающие табличное значение параметры строго типизированы, и проверка их структуры происходит автоматически. Размер возвращающих табличное значение параметров ограничен только объемом памяти сервера.  
  
> [!NOTE]
>  Невозможно вернуть данные в параметре, возвращающем табличное значение. Возвращающие табличное значение параметры являются только входными. ключевое слово OUTPUT не поддерживается.  
  
Дополнительные сведения о возвращающих табличное значение параметрах см. в следующих ресурсах.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Возвращающие табличное значение параметры (ядро СУБД)](https://go.microsoft.com/fwlink/?LinkId=98363) в электронной документации на SQL Server|Описывает создание и использование возвращающих табличное значение параметров.|  
|[Определяемые пользователем табличные типы](https://go.microsoft.com/fwlink/?LinkId=98364) в Электронная документация на SQL Server|Описывает использование определяемых пользователем табличных типов для объявления возвращающих табличное значение параметров.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Передача нескольких строк в предыдущих версиях SQL Server  
До появления в SQL Server 2008 параметров, возвращающих табличное значение, были ограниченны возможности передачи нескольких строк данных в хранимую процедуру или параметризованную команду SQL. Разработчик может выбрать один из следующих вариантов передачи нескольких строк на сервер:  
  
- Используйте ряд отдельных параметров, чтобы представить значения в нескольких столбцах и строках данных. Объем данных, которые могут быть переданы с помощью этого метода, ограничено количеством допустимых параметров. В процедурах SQL Server можно использовать не более 2100 параметров. Логика на стороне сервера необходима для того, чтобы собрать эти отдельные значения в табличную переменную или временную таблицу для обработки.  
  
- Объединить несколько значений данных в строки с разделителями или документы XML, а затем передать эти текстовые значения в процедуру или инструкцию. Для этого необходимо, чтобы процедура или инструкция включала логику, необходимую для проверки структуры данных и отменяя объединение значений.  
  
- Создайте ряд отдельных инструкций SQL для изменений данных, влияющих на несколько строк, например, созданных путем вызова метода `Update` <xref:Microsoft.Data.SqlClient.SqlDataAdapter>. Изменения могут отправляться на сервер по отдельности или объединяться в группы. Однако даже при отправке в пакетах, содержащих несколько инструкций, каждая инструкция выполняется отдельно на сервере.  
  
- Используйте служебную программу `bcp` или объект <xref:Microsoft.Data.SqlClient.SqlBulkCopy> для загрузки в таблицу нескольких строк данных. Хотя этот метод очень эффективен, он не поддерживает обработку на стороне сервера, если данные не загружаются во временную таблицу или табличную переменную.  
  
## <a name="creating-table-valued-parameter-types"></a>Создание типов параметров, возвращающих табличное значение  
Возвращающие табличное значение параметры основаны на строго типизированных табличных структурах, заданных с помощью инструкций Transact-SQL CREATE TYPE. Перед использованием в клиентских приложениях возвращающих табличное значение параметров в SQL Server необходимо создать табличный тип и определить структуру. Дополнительные сведения о создании типов таблиц см. в разделе [Определяемые пользователем табличные типы](https://go.microsoft.com/fwlink/?LinkID=98364) электронной документации на SQL Server.  
  
Следующая инструкция создает табличный тип с именем Категоритаблетипе, состоящий из столбцов CategoryID и CategoryName:  
  
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
Возвращающие табличные значения параметры можно использовать в изменениях данных на основе наборов, которые влияют на несколько строк, выполняя одну инструкцию. Например, можно выбрать все строки в возвращающем табличное значение параметр и вставить их в таблицу базы данных. Кроме того, можно создать инструкцию UPDATE, присоединив возвращающий табличное значение параметр к таблице, которую необходимо обновить.  
  
В приведенной ниже инструкции Transact-SQL UPDATE демонстрируется соединение возвращающего табличное значение параметра с таблицей Categories. При использовании возвращающего табличное значение параметра с СОЕДИНЕНИЕм в предложении FROM необходимо также присвоить ему псевдоним, как показано здесь, где параметр с табличным значением имеет псевдоним "EC":  
  
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
Существует несколько ограничений для возвращающих табличное значение параметров.  
  
- Возвращающие табличное значение параметры нельзя передавать [определяемым пользователем функциям CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md).  
  
- Возвращающие табличные значения параметры могут индексироваться только для поддержки ограничений UNIQUE или PRIMARY KEY. SQL Server не ведет статистику возвращающих табличные значения параметров.  
  
- В коде Transact-SQL возвращающие табличное значение параметры предназначены только для чтения. Нельзя обновить значения столбцов в строках возвращающего табличное значение параметра, а также вставлять или удалять строки. Чтобы изменить данные, передаваемые в хранимую процедуру или параметризованную инструкцию в возвращающем табличное значение параметре, необходимо вставить данные во временную таблицу или в табличную переменную.  
  
- Нельзя использовать инструкции ALTER TABLE для изменения структуры возвращающих табличное значение параметров.  
  
## <a name="configuring-a-sqlparameter-example"></a>Пример настройки элемента SqlParameter  
Поставщик <xref:Microsoft.Data.SqlClient> поддерживает заполнение возвращающих табличное значение параметров из объектов <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> или <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.Data.SqlClient.Server.SqlDataRecord>. Необходимо указать имя типа возвращающего табличное значение параметра с помощью свойства <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> объекта <xref:Microsoft.Data.SqlClient.SqlParameter>. `TypeName` должно совпадать с именем совместимого типа, ранее созданного на сервере. В следующем фрагменте кода показано, как настроить <xref:Microsoft.Data.SqlClient.SqlParameter> для вставки данных.  
 
В следующем примере переменная `addedCategories` содержит <xref:System.Data.DataTable>. Чтобы увидеть, как заполняется переменная, см. примеры в следующем разделе [передача возвращающего табличное значение параметра хранимой процедуре](#passing).

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
В этом примере показано, как передавать данные возвращающего табличное значение параметра в хранимую процедуру. Код извлекает добавленные строки в новый <xref:System.Data.DataTable> с помощью метода <xref:System.Data.DataTable.GetChanges%2A>. Затем код определяет <xref:Microsoft.Data.SqlClient.SqlCommand>, устанавливая для свойства <xref:Microsoft.Data.SqlClient.SqlCommand.CommandType%2A> значение <xref:System.Data.CommandType.StoredProcedure>. <xref:Microsoft.Data.SqlClient.SqlParameter> заполняется с помощью метода <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A>, а <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> устанавливается в `Structured`. Затем <xref:Microsoft.Data.SqlClient.SqlCommand> выполняется с помощью метода <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
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
 В следующем примере показано, как вставить данные в dbo. Таблицы Categories с помощью инструкции INSERT с вложенным запросом SELECT, имеющим в качестве источника данных возвращающий табличное значение параметр. При передаче возвращающего табличное значение параметра в параметризованную инструкцию SQL необходимо указать имя типа для возвращающего табличное значение параметра с помощью нового свойства <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> <xref:Microsoft.Data.SqlClient.SqlParameter>. Этот `TypeName` должен совпадать с именем совместимого типа, ранее созданного на сервере. Код в этом примере использует свойство `TypeName` для ссылки на структуру типа, определенную в dbo. Категоритаблетипе.  
  
> [!NOTE]
>  При указании значения для столбца идентификаторов в возвращающем табличное значение параметре необходимо выполнить инструкцию SET IDENTITY_INSERT для сеанса.  
  
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
Также для передачи строк данных в возвращающий табличное значение параметр можно использовать любой производный от <xref:System.Data.Common.DbDataReader> объект. В следующем фрагменте кода демонстрируется получение данных из базы данных Oracle с помощью <xref:System.Data.OracleClient.OracleCommand> и <xref:System.Data.OracleClient.OracleDataReader>. Затем код настраивает <xref:Microsoft.Data.SqlClient.SqlCommand> для вызова хранимой процедуры с одним входным параметром. Свойству <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> <xref:Microsoft.Data.SqlClient.SqlParameter> присваивается значение `Structured`. <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> передает результирующий набор `OracleDataReader` в хранимую процедуру в виде возвращающего табличное значение параметра.  
  
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
