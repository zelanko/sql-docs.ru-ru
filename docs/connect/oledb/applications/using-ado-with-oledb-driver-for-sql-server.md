---
title: Использование объектов ADO с драйвером OLE DB для SQL Server | Документация Майкрософт
description: Использование объектов ADO с драйвером OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 1906ad25e9bb170b8979f44757ec5742ad9ec6c4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778044"
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>Использование объектов ADO с драйвером OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Для реализации новых возможностей [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (в частности, множественного активного результирующего набора (MARS), уведомлений о запросах, пользовательских типов данных и нового типа данных **xml**) существующие приложения, использующие объекты данных ActiveX (ADO), должны использовать драйвер OLE DB для SQL Server в качестве поставщика доступа к данным.  
  
 Чтобы позволить ADO использовать новые возможности последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], были внесены некоторые улучшения в драйвер OLE DB для SQL Server, расширяющие базовую функциональность OLE DB. Эти улучшения позволяют приложениям ADO использовать новые возможности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и применять два типа данных, появившихся в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** и **udt**. Эти улучшения также используют усовершенствования типов данных **varchar**, **nvarchar** и **varbinary**. Драйвер OLE DB для SQL Server добавляет свойство инициализации SSPROP_INIT_DATATYPECOMPATIBILITY к набору свойств DBPROPSET_SQLSERVERDBINIT для использования приложениями ADO, чтобы новые типы данных предоставлялись совместимым с ADO образом. Кроме того, драйвер OLE DB для SQL Server также определяет новое ключевое слово строки подключения с именем **DataTypeCompatibility** , задается в строке подключения.  

> [!NOTE]  
>  Существующие приложения ADO могут обращаться к полям XML определяемых пользователем типов, текстовым полям больших значений и полям двоичных значений, а также обновлять их значения с помощью поставщика SQLOLEDB. Новые типы данных **varchar(max)** , **nvarchar(max)** и **varbinary(max)** увеличенного размера возвращаются как типы ADO **adLongVarChar**, **adLongVarWChar** и **adLongVarBinary** соответственно. XML-столбцы возвращаются как **adLongVarChar**, а столбцы пользовательских типов возвращаются как **adVarBinary**. Тем не менее, если вы используете драйвер OLE DB для SQL Server (MSOLEDBSQL) вместо SQLOLEDB, необходимо обязательно установите **DataTypeCompatibility** ключевое слово «80», чтобы новые типы данных правильно сопоставлялись с типами данных ADO.  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>Включение драйвера OLE DB для SQL Server из ADO  
 Чтобы обеспечить использование драйвера OLE DB для SQL Server, приложения ADO должны включать следующие ключевые слова в строки подключения:  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 Дополнительные сведения о ключевых словах строки подключения см. в статье [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

 Ниже приведен пример создания строки подключения ADO, полностью обеспечивающей работу с драйвером OLE DB для SQL Server, в том числе включающей поддержку функции MARS.  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  

## <a name="examples"></a>Примеры  
 В следующих разделах приведены примеры того, как использовать ADO с драйвером OLE DB для SQL Server.  

### <a name="retrieving-xml-column-data"></a>Получение данных XML-столбца  
 В этом примере набор записей используется для извлечения и отображения данных из XML-столбца в образце базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks**.  

```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  

' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  

con.Close  
Set con = Nothing  
```  

> [!NOTE]  
>  Фильтрация наборов записей для XML-столбцов не поддерживается. При попытке ее использования возвращается ошибка.  

### <a name="retrieving-udt-column-data"></a>Получение данных столбца определяемого пользователем типа  
 В этом примере объект **Command** используется для выполнения запроса SQL, который возвращает пользовательский тип, после чего данные пользовательского типа обновляются и вставляются в базу данных. В этом примере предполагается, что пользовательский тип **Point** был заранее зарегистрирован в базе данных.  

```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  

' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  

' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  

con.Close  
Set con = Nothing  
```  

### <a name="enabling-and-using-mars"></a>Включение и использование режима MARS  
 В этом примере строка подключения составляется таким образом, чтобы включить режим MARS для драйвера OLE DB для SQL Server, затем создаются два объекта набора записей для выполнения в том же соединении.  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  

Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  

Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  

con.Close  
Set con = Nothing  
```  

 В предыдущих версиях поставщика OLE DB этот код вызвал бы создание неявного соединения при втором выполнении, так как в одном соединении можно было открыть только один активный набор результатов. Поскольку неявное соединение не включалось в пул соединений OLE DB, это вызывало дополнительные издержки. Когда драйвер OLE DB для SQL Server обеспечивает поддержку функции MARS, в одном соединении может быть несколько активных результатов.  

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
