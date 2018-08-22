---
title: Использование ADO с SQL Server Native Client | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
ms.openlocfilehash: 6fb21b7859b3666ef4d62743cb8f641745c33daf
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395577"
---
# <a name="using-ado-with-sql-server-native-client"></a>Использование ADO с собственным клиентом SQL Server
  Чтобы воспользоваться преимуществами новых возможностей, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] несколько активных результирующих наборов (MARS), уведомления о запросах, определяемые пользователем типы (UDT) или новый **xml** тип данных, существующие приложения, использующие ActiveX Data Objects (ADO) следует использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента в качестве поставщика доступа к данным.  
  
 Если применение новых функций [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] не требуется, то можно не использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а продолжать работу с текущим поставщиком доступа к данным (обычно это SQLOLEDB). Если производится улучшение существующего приложения и необходимо задействовать новые функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], следует использовать поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если проектируется новое приложение, рекомендуется использовать ADO.NET и поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] вместо собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для доступа ко всем новым функциям последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения о поставщике данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в документации по пакету SDK платформы .NET Framework для ADO.NET.  
  
 Чтобы позволить ADO использовать новые возможности последних версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], были внесены некоторые улучшения в поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], расширяющие базовую функциональность OLE DB. Эти улучшения позволяют приложениям ADO использовать новые возможности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и применять два типа данных, появившихся в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** и **udt**. Эти улучшения также используют усовершенствования типов данных **varchar**, **nvarchar** и **varbinary**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент добавляет свойство инициализации SSPROP_INIT_DATATYPECOMPATIBILITY к набору свойств DBPROPSET_SQLSERVERDBINIT для использования приложениями ADO, чтобы новые типы данных представлены в совместимым с ADO образом. Кроме того [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента также определяет новое ключевое слово строки подключения с именем `DataTypeCompatibility` , задается в строке подключения.  
  
> [!NOTE]  
>  Существующие приложения ADO могут обращаться к полям XML определяемых пользователем типов, текстовым полям больших значений и полям двоичных значений, а также обновлять их значения с помощью поставщика SQLOLEDB. Новые типы данных **varchar(max)**, **nvarchar(max)** и **varbinary(max)** увеличенного размера возвращаются как типы ADO **adLongVarChar**, **adLongVarWChar** и **adLongVarBinary** соответственно. XML-столбцы возвращаются как **adLongVarChar**, а столбцы пользовательских типов возвращаются как **adVarBinary**. Однако при использовании поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SQLNCLI11) вместо SQLOLEDB обязательно следует установить для ключевого слова `DataTypeCompatibility` значение «80», чтобы новые типы данных правильно сопоставлялись с типами данных ADO.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Включение собственного клиента SQL Server из ADO  
 Чтобы включить использование [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, приложения ADO должны реализовать следующие ключевые слова в строке подключения:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Дополнительные сведения о ADO поддерживается в ключевых словах строк соединений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, см. в разделе [Using Connection String Keywords with SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Ниже приведен пример создания строки соединения ADO, полностью обеспечивающей работу с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, в том числе включающей поддержку функциональности MARS:  
  
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
 В этом примере строка соединения составляется Чтобы включить режим MARS [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента и затем два объекта набора записей создаются для выполнения, в том же соединении.  
  
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
  
 В предыдущих версиях поставщика OLE DB этот код вызвал бы создание неявного соединения при втором выполнении, так как в одном соединении можно было открыть только один активный набор результатов. Поскольку неявное соединение не включалось в пул соединений OLE DB, это вызывало дополнительные издержки. С помощью функции MARS предоставляемые [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента, вы получаете несколько активных наборов результатов в одном соединении.  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
