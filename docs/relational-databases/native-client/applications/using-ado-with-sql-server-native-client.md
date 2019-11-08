---
title: Использование ADO с SQL Server Native Client | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a7dc196adfa3d43563f1d8755efac2bf363bb88c
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761521"
---
# <a name="using-ado-with-sql-server-native-client"></a>Использование ADO с собственным клиентом SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы воспользоваться преимуществами новых функций, появившихся в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] таких как режим MARS, уведомления о запросах, определяемые пользователем типы или новый тип данных **XML** , существующие приложения, использующие объекты данных ACTIVEX (ADO), должны использовать Поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента OLE DB в качестве поставщика доступа к данным.  
  
 Если применение новых функций [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] не требуется, то можно не использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а продолжать работу с текущим поставщиком доступа к данным (обычно это SQLOLEDB). Если производится улучшение существующего приложения и необходимо задействовать новые функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], следует использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если проектируется новое приложение, рекомендуется использовать ADO.NET и поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вместо собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для доступа ко всем новым функциям последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения о поставщике данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в документации по пакету SDK платформы .NET Framework для ADO.NET.  
  
 Чтобы позволить ADO использовать новые возможности последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], были внесены некоторые улучшения в поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], расширяющие базовую функциональность OLE DB. Эти улучшения позволяют приложениям ADO использовать новые возможности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и применять два типа данных, появившихся в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** и **udt**. Эти улучшения также используют усовершенствования типов данных **varchar**, **nvarchar** и **varbinary**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client добавляет свойство инициализации SSPROP_INIT_DATATYPECOMPATIBILITY в свойство DBPROPSET_SQLSERVERDBINIT, заданное для использования приложениями ADO, чтобы новые типы данных были представлены способом, совместимым с ADO. Кроме того, поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента OLE DB также определяет новое ключевое слово строки подключения с именем **DataTypeCompatibility диспетчера соединений** , заданное в строке подключения.  
  
> [!NOTE]  
>  Существующие приложения ADO могут обращаться к полям XML определяемых пользователем типов, текстовым полям больших значений и полям двоичных значений, а также обновлять их значения с помощью поставщика SQLOLEDB. Новые типы данных **varchar(max)** , **nvarchar(max)** и **varbinary(max)** увеличенного размера возвращаются как типы ADO **adLongVarChar**, **adLongVarWChar** и **adLongVarBinary** соответственно. XML-столбцы возвращаются как **adLongVarChar**, а столбцы пользовательских типов возвращаются как **adVarBinary**. Однако, если вместо SQLOLEDB используется поставщик [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (SQLNCLI11), необходимо обязательно задать для ключевого слова **DataTypeCompatibility диспетчера соединений** значение "80", чтобы новые типы данных правильно сопоставлялись с ТИПАМИ данных ADO.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Включение собственного клиента SQL Server из ADO  
 Чтобы включить использование [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента, приложениям ADO потребуется реализовать следующие ключевые слова в строках подключения:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Дополнительные сведения о ключевых словах строки соединений ADO, поддерживаемых в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Ниже приведен пример установки строки подключения ADO, которая полностью включена для работы с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственным клиентом, включая включение функции MARS.  
  
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
 В следующих разделах приведены примеры использования ADO с поставщиком [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB.  
  
### <a name="retrieving-xml-column-data"></a>Получение данных XML-столбца  
 В этом примере набор записей используется для извлечения и отображения данных из XML-столбца в образце базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks**.  
  
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
 В этом примере строка подключения создается для включения режима MARS с помощью поставщика [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента OLE DB, а затем создаются два объекта набора записей для выполнения с использованием одного и того же соединения.  
  
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
  
 В предыдущих версиях поставщика OLE DB этот код вызвал бы создание неявного соединения при втором выполнении, так как в одном соединении можно было открыть только один активный набор результатов. Поскольку неявное соединение не включалось в пул соединений OLE DB, это вызывало дополнительные издержки. С помощью функции MARS, предоставляемой поставщиком OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], вы получаете несколько активных результатов для одного соединения.  
  
## <a name="see-also"></a>См. также раздел  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
