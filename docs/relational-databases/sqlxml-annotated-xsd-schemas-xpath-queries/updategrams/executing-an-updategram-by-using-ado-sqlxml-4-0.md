---
title: Выполнение диаграммы обновления с помощью ADO (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO [SQLXML]
- updategrams [SQLXML], ADO
- executing updategrams [SQLXML]
ms.assetid: 78610ca0-f763-45fc-ac64-da5c192cc3e5
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 95272db4677cafad6f1e3c84f14b5705dd5f4718
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051462"
---
# <a name="executing-an-updategram-by-using-ado-sqlxml-40"></a>Выполнение диаграммы обновления при помощи ADO (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Следующее приложение на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic использует ADO для установки соединения с экземпляром Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и выполняет диаграмму обновления. Диаграмма обновления изменяет фамилию конкретного сотрудника. В примере используется образец базы данных AdventureWorks.  
  
 В этом образце приложения происходит следующее.  
  
-   **Conn** объекта (**ADODB. Подключение**) подключается к запущенному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на заданном сервере.  
  
-   **Cmd** объекта (**ADODB.Command**) выполняется в рамках установленного подключения.  
  
-   В качестве диалекта команды задано значение DBGUID_MSSQLXML.  
  
-   Диаграмма обновления копируется в поток команды (**strmIn**).  
  
-   Выходной поток команды присваивается **StrmOut** объекта (**ADODB. Stream**), который получает все возвращаемых данных.  
  
-   Наконец выполняется команда (диаграмма обновления).  
  
 Ниже представлен образец кода.  
  
```vb  
Private Sub Form_Load()  
  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmIn As New ADODB.Stream  
  Dim strmOut As New ADODB.Stream  
  Dim SQLxml As String  
  
  ' Open a connection to the instance of SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=(local); database=AdventureWorks; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  
  ' Build the command string in the form of an XML template.  
    SQLxml = "<ROOT xmlns:updg='urn:schemas-microsoft-com:xml-updategram' >"  
    SQLxml = SQLxml & "  <updg:sync updg:nullvalue='IsNULL'>"  
    SQLxml = SQLxml & "    <updg:before>"  
    SQLxml = SQLxml & "       <Person.Contact ContactID='64' Title='IsNULL'/>"  
    SQLxml = SQLxml & "    </updg:before>"  
    SQLxml = SQLxml & "    <updg:after>"  
    SQLxml = SQLxml & "       <Person.Contact ContactID='64' Title='Mr.'/>"  
    SQLxml = SQLxml & "    </updg:after>"  
    SQLxml = SQLxml & "  </updg:sync>"  
    SQLxml = SQLxml & "</ROOT>"  
  
  ' Set the command dialect to DBGUID_MSSQLXML.  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
  ' Open the command stream and write our template to it.  
  strmIn.Open  
  strmIn.WriteText SQLxml  
  strmIn.Position = 0  
  
  Set cmd.CommandStream = strmIn  
  
  ' Execute the command, open the return stream, and read the result.  
  strmOut.Open  
  strmOut.LineSeparator = adCRLF  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Debug.Print strmOut.ReadText  
  strmOut.Close  
  strmIn.Close  
  
End Sub  
  
```  
  
> [!NOTE]  
>  Если SQLXML используется из ADO для выполнения диаграмм обновления, которые задают схему XSD, в объекте соединения необходимо присвоить свойству `SQLXML Version` значение `SQLXML.4.0`, как показано в следующем примере кода.  
>   
>  `conn.Properties("SQLXML Version") = "SQLXML.4.0"`  
  
## <a name="specifying-a-mapping-schema-for-the-updategram"></a>Указание схемы сопоставления для диаграммы обновления  
 В этом примере показано, как задать и использовать схему сопоставления в диаграмме обновления.  
  
 Сохраните на диск следующую схему XSD (EmpSchema.xml) и убедитесь, что обновлен заданный в коде путь к расположению схемы сопоставления. Этот код предполагает, что схема сохранена на диске C: в папке Schemas.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
        <xsd:attribute name="CID"    
                       sql:field="ContactID"   
                       type="xsd:string" />   
        <xsd:attribute name="MName"    
                       sql:field="MiddleName"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Поскольку можно задать как схему XSD, так и схему XDR, приводим эквивалентную схему XDR:  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Contact" sql:relation="Person.Contact" >  
       <AttributeType name="CID" />  
       <AttributeType name="MName" />  
  
       <attribute type="CID" sql:field="ContactID" />  
       <attribute type="MName" sql:field="MiddleName" />  
     </ElementType>  
   </Schema>   
```  
  
 Следующий код Visual Basic выполняет диаграмму обновления, связанную со схемой сопоставления. Диаграмма обновления изменяет отчество контакта 1 в таблице Person.Contact.  
  
```vb  
Private Sub Form_Load()  
    Dim cmd As New ADODB.Command  
    Dim conn As New ADODB.Connection  
    Dim strmIn As New ADODB.Stream  
    Dim strmOut As New ADODB.Stream  
  
    ' Open a connection to the SQL Server.  
    conn.Provider = "SQLOLEDB"  
    conn.Open "server=(local); database=AdventureWorks; Integrated Security='SSPI' ;"  
    conn.Properties("SQLXML Version") = "SQLXML.4.0"  
    Set cmd.ActiveConnection = conn  
  
    ' Open the command stream and write the template to it.  
    strmIn.Open  
    strmIn.WriteText "<ROOT xmlns:updg='urn:schemas-microsoft-com:xml-updategram' >"  
    strmIn.WriteText "  <updg:sync mapping-schema='C:\Schemas\EmpSchema.xml' >"  
    strmIn.WriteText "      <updg:before>"  
    strmIn.WriteText "          <Contact CID='1' />"  
    strmIn.WriteText "      </updg:before>"  
    strmIn.WriteText "      <updg:after>"  
    strmIn.WriteText "          <Contact MName='M.'/>"  
    strmIn.WriteText "      </updg:after>"  
    strmIn.WriteText "  </updg:sync>"  
    strmIn.WriteText "</ROOT>"  
  
    ' Set the command dialect to XML.  
    cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
    strmIn.Position = 0  
    Set cmd.CommandStream = strmIn  
  
    ' Execute the command, open the return stream, and read the result.  
    strmOut.Open  
    strmOut.LineSeparator = adCRLF  
    cmd.Properties("Output Stream").Value = strmOut  
    cmd.Execute , , adExecuteStream  
    strmOut.Position = 0  
    Debug.Print strmOut.ReadText  
    strmOut.Close  
    strmIn.Close  
    conn.Close  
End Sub  
```  
  
## <a name="passing-parameters"></a>Передача параметров  
 В представленных выше приложениях Visual Basic отсутствует передача параметров. В этом приложении **ContactID** и **MiddleName** значения передаются в качестве параметризованного входа в диаграмму обновления.  
  
```vb  
Private Sub Form_Load()  
  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmIn As New ADODB.Stream  
  Dim strmOut As New ADODB.Stream  
  Dim InputContactID As String  
  Dim InputMiddleName As String  
  
  InputContactID = "1"  
  InputMiddleName = "Q."  
  
  ' Open a connection to the instance of SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=(local); database=AdventureWorks; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  
  ' Build the command string in the form of an XML template.  
  SQLxml = "<ROOT xmlns:updg='urn:schemas-microsoft-com:xml-updategram' >"  
  SQLxml = SQLxml & "<updg:header>"  
  SQLxml = SQLxml & "<updg:param name='ContactID'/>"  
  SQLxml = SQLxml & "<updg:param name='MiddleName' />"  
  SQLxml = SQLxml & "</updg:header>"  
  SQLxml = SQLxml & "<updg:sync >"  
  SQLxml = SQLxml & " <updg:before>"  
  SQLxml = SQLxml & "   <Person.Contact ContactID='$ContactID' />"  
  SQLxml = SQLxml & "</updg:before>"  
  SQLxml = SQLxml & "<updg:after>"  
  SQLxml = SQLxml & "<Person.Contact MiddleName='$MiddleName' />"  
  SQLxml = SQLxml & "</updg:after>"  
  SQLxml = SQLxml & "</updg:sync>"  
  SQLxml = SQLxml & "</ROOT>"  
  
  ' Set the command dialect to XML.  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
  ' Open the command stream and write the template to it.  
  strmIn.Open  
  strmIn.WriteText SQLxml  
  strmIn.Position = 0  
  
  Set cmd.CommandStream = strmIn  
  
  ' Execute the command, open the return stream, and read the result.  
  strmOut.Open  
  strmOut.LineSeparator = adCRLF  
  cmd.NamedParameters = True  
  cmd.Parameters.Append cmd.CreateParameter("@ContactID", adBSTR, adParamInput, 1, InputContactID)  
  cmd.Parameters.Append cmd.CreateParameter("@MiddleName", adBSTR, adParamInput, 7, InputMiddleName)  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Debug.Print strmOut.ReadText  
  
End Sub  
```  
  
  
