---
title: Использование ADO с драйвером OLE DB для SQL Server | Документы Microsoft
description: Использование ADO с драйвером OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3003fd77624f7e304f8e3f493148475c1187a86b
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>Использование ADO с драйвером OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы воспользоваться преимуществами новых возможностей, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] как несколько активных результирующих наборов (MARS), уведомления о запросах, определяемых пользователем типов (UDT) или новый **xml** тип данных, существующих приложений, использующих ActiveX Data Objects (ADO) следует использовать драйвер OLE DB для SQL Server в качестве поставщика доступа к данным.  
  
 Чтобы позволить ADO использовать новые возможности последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], были внесены некоторые улучшения драйвер OLE DB для SQL Server, которая расширяет основные функции OLE DB. Эти улучшения позволяют приложениям ADO использовать новые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функции и использовать два типа данных, введенных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** и **определяемого пользователем типа**. Эти улучшения также используют усовершенствования **varchar**, **nvarchar**, и **varbinary** типов данных. Драйвер OLE DB для SQL Server добавляет свойство инициализации SSPROP_INIT_DATATYPECOMPATIBILITY к набору свойств DBPROPSET_SQLSERVERDBINIT для использования приложениями ADO, чтобы новые типы данных, предоставляются способом, совместимым с ADO. Кроме того, драйвер OLE DB для SQL Server также определяет новое ключевое слово строки подключения с именем **DataTypeCompatibility** , задается в строке подключения.  

> [!NOTE]  
>  Существующие приложения ADO могут обращаться к полям XML определяемых пользователем типов, текстовым полям больших значений и полям двоичных значений, а также обновлять их значения с помощью поставщика SQLOLEDB. Новый больше **varchar(max)**, **nvarchar(max)**, и **varbinary(max)** типы данных, возвращаются как типы ADO **adLongVarChar**, **adLongVarWChar** и **adLongVarBinary** соответственно. XML-столбцы возвращаются в виде **adLongVarChar**, а столбцы определяемых пользователем ТИПОВ возвращаются как **adVarBinary**. Тем не менее, если вы используете драйвер OLE DB для SQL Server (MSOLEDBSQL) вместо SQLOLEDB, необходимо обязательно установите **DataTypeCompatibility** ключевое слово «80», чтобы новые типы данных правильно сопоставлялись с типами данных ADO.  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>Включение драйвер OLE DB для SQL Server из ADO  
 Чтобы включить использование драйвер OLE DB для SQL Server, приложения ADO необходимо реализовать следующие ключевые слова в строке соединения:  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 Дополнительные сведения о ADO поддерживается в драйвер OLE DB для SQL Server, ключевых словах строк соединений. в разделе [с помощью ключевых слов строки подключения с драйвер OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

 Ниже приведен пример создания строки соединения ADO, полностью включены для драйвер OLE DB для SQL Server, в том числе включение функции MARS:  

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
 В этом примере набор записей используется для извлечения и отображения данных из XML-столбец [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** образца базы данных.  

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
 В этом примере **команда** объект используется для выполнения запроса SQL, который возвращает определяемый пользователем тип, определяемый пользователем тип данных обновляется и затем новые данные вставляются в базу данных. В этом примере предполагается, что **точки** определяемый пользователем тип уже был зарегистрирован в базе данных.  

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
 В этом примере строка соединения составляется для включения режима MARS через драйвер OLE DB для SQL Server и затем создаются два объекта набора записей для выполнения в том же соединении.  

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

 В предыдущих версиях поставщика OLE DB этот код вызвал бы создание неявного соединения при втором выполнении, так как в одном соединении можно было открыть только один активный набор результатов. Поскольку неявное соединение не включалось в пул соединений OLE DB, это вызывало дополнительные издержки. С помощью функции режима MARS, предоставляемые драйвер OLE DB для SQL Server вы получаете несколько активных наборов результатов в одном соединении.  

## <a name="see-also"></a>См. также  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
