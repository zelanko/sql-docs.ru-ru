---
title: Использование ADO
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94c241e4dd089b0db667e5b24dbde541584bba41
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388265"
---
# <a name="using-ado-with-sql-server-native-client"></a>Использование ADO с собственным клиентом SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для того, чтобы воспользоваться [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] новыми функциями, введенными в таких областях, как несколько активных наборов результатов (MARS), уведомления о запросах, пользовательские типы (UDT) или новый тип данных **xml,** существующие приложения, которые используют объекты данных ActiveX (ADO), должны использовать поставщика [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB в качестве поставщика доступа к данным.  
  
 Если применение новых функций [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] не требуется, то можно не использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а продолжать работу с текущим поставщиком доступа к данным (обычно это SQLOLEDB). Если производится улучшение существующего приложения и необходимо задействовать новые функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], следует использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если проектируется новое приложение, рекомендуется использовать ADO.NET и поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вместо собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для доступа ко всем новым функциям последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения о поставщике данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в документации по пакету SDK платформы .NET Framework для ADO.NET.  
  
 Чтобы позволить ADO использовать новые возможности последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], были внесены некоторые улучшения в поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], расширяющие базовую функциональность OLE DB. Эти улучшения позволяют приложениям ADO использовать новые возможности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и применять два типа данных, появившихся в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** и **udt**. Эти улучшения также используют усовершенствования типов данных **varchar**, **nvarchar** и **varbinary**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Родной клиент добавляет свойство SSPROP_INIT_DATATYPECOMPATIBILITY инициализации в свойство DBPROPSET_SQLSERVERDBINIT, установленное для использования приложениями ADO, чтобы новые типы данных были подвержены совместимости с ADO. Кроме того, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик Native Client OLE DB также определяет новое ключевое слово строки соединения под названием **DataTypeCompatibility,** которое устанавливается в строке соединения.  
  
> [!NOTE]  
>  Существующие приложения ADO могут обращаться к полям XML определяемых пользователем типов, текстовым полям больших значений и полям двоичных значений, а также обновлять их значения с помощью поставщика SQLOLEDB. Новые типы данных **varchar(max)**, **nvarchar(max)** и **varbinary(max)** увеличенного размера возвращаются как типы ADO **adLongVarChar**, **adLongVarWChar** и **adLongVarBinary** соответственно. XML-столбцы возвращаются как **adLongVarChar**, а столбцы пользовательских типов возвращаются как **adVarBinary**. Однако, если [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вы используете поставщика Native Client OLE DB (S'LNCLI11) вместо S'LOLEDB, необходимо убедиться, что необходимо установить ключевое слово **DataTypeCompatibility** на "80", чтобы новые типы данных правильно сопоставили с типами данных ADO.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Включение собственного клиента SQL Server из ADO  
 Для обеспечения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использования Native Client приложениям ADO необходимо будет реализовать следующие ключевые слова в строках соединения:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Для получения дополнительной информации о ключевых [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] словах строки aDO-соединений, поддерживаемых в Native Client, см. [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
 Ниже приводится пример создания строки подключения ADO, которая [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] полностью позволяет работать с Native Client, включая включение функции MARS:  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a>Примеры  
 В следующих разделах приводятся примеры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] того, как можно использовать ADO с поставщиком Native Client OLE DB.  
  
### <a name="retrieving-xml-column-data"></a>Получение данных XML-столбца  
 В этом примере набор записей используется для извлечения и отображения данных из XML-столбца в тестовой базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks**.  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
 В этом примере строка соединения построена [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для включения MARS через поставщика Native Client OLE DB, а затем для выполнения с помощью одного и того же соединения создаются два объекта записей.  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
 В предыдущих версиях поставщика OLE DB этот код вызвал бы создание неявного соединения при втором выполнении, так как в одном соединении можно было открыть только один активный набор результатов. Поскольку неявное соединение не включалось в пул соединений OLE DB, это вызывало дополнительные издержки. С функцией MARS, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выставленной поставщиком Native Client OLE DB, вы получаете несколько активных результатов на одном подключении.  
  
## <a name="see-also"></a>См. также:  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
