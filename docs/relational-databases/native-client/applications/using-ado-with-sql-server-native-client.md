---
title: Использование ADO с собственным клиентом SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4153097e55d2cdcf77fcfdf880ec7a0181e3d9e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-ado-with-sql-server-native-client"></a>Использование ADO с собственным клиентом SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Чтобы воспользоваться преимуществами новых возможностей, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] как несколько активных результирующих наборов (MARS), уведомления о запросах, определяемых пользователем типов (UDT) или новый **xml** тип данных, существующих приложений, использующих ActiveX Data Objects (ADO) следует использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента в качестве поставщика доступа к данным.  
  
 Если применение новых функций [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] не требуется, то можно не использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а продолжать работу с текущим поставщиком доступа к данным (обычно это SQLOLEDB). Если производится улучшение существующего приложения и необходимо задействовать новые функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], следует использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если проектируется новое приложение, рекомендуется использовать ADO.NET и поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вместо собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для доступа ко всем новым функциям последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения о поставщике данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в документации по пакету SDK платформы .NET Framework для ADO.NET.  
  
 Чтобы позволить ADO использовать новые возможности последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], были внесены некоторые улучшения в поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], расширяющие базовую функциональность OLE DB. Эти улучшения позволяют приложениям ADO использовать новые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функции и использовать два типа данных, введенных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** и **определяемого пользователем типа**. Эти улучшения также используют усовершенствования **varchar**, **nvarchar**, и **varbinary** типов данных. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент добавляет свойство инициализации SSPROP_INIT_DATATYPECOMPATIBILITY к набору свойств DBPROPSET_SQLSERVERDBINIT для использования приложениями ADO, чтобы новые типы данных, предоставляются способом, совместимым с ADO. Кроме того [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента также определяет новое ключевое слово строки подключения с именем **DataTypeCompatibility** , задается в строке подключения.  
  
> [!NOTE]  
>  Существующие приложения ADO могут обращаться к полям XML определяемых пользователем типов, текстовым полям больших значений и полям двоичных значений, а также обновлять их значения с помощью поставщика SQLOLEDB. Новый больше **varchar(max)**, **nvarchar(max)**, и **varbinary(max)** типы данных, возвращаются как типы ADO **adLongVarChar**, **adLongVarWChar** и **adLongVarBinary** соответственно. XML-столбцы возвращаются в виде **adLongVarChar**, а столбцы определяемых пользователем ТИПОВ возвращаются как **adVarBinary**. Тем не менее если вы используете [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента (SQLNCLI11) вместо SQLOLEDB, необходимо обязательно установите **DataTypeCompatibility** ключевое слово «80», чтобы новые типы данных правильно сопоставлялись данными ADO типы.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Включение собственного клиента SQL Server из ADO  
 Чтобы включить использование [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента приложения ADO должны реализовать следующие ключевые слова в строке соединения:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Дополнительные сведения о ADO поддерживается в ключевых словах строк соединений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client см. в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Ниже приведен пример создания строки соединения ADO, полностью включены для работы с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, в том числе включение функции MARS:  
  
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
 В следующих разделах приведены примеры того, как можно использовать ADO с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
### <a name="retrieving-xml-column-data"></a>Получение данных XML-столбца  
 В этом примере набор записей используется для извлечения и отображения данных из XML-столбец [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** образца базы данных.  
  
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
 В этом примере создается строка подключения, чтобы включить режим MARS [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента и затем два объекта набора записей создаются для выполнения в том же соединении.  
  
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
  
 В предыдущих версиях поставщика OLE DB этот код вызвал бы создание неявного соединения при втором выполнении, так как в одном соединении можно было открыть только один активный набор результатов. Поскольку неявное соединение не включалось в пул соединений OLE DB, это вызывало дополнительные издержки. С помощью функции MARS предоставляемые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, вы получаете несколько активных наборов результатов одно подключение.  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
