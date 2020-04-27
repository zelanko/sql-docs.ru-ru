---
title: Пример методов Execute, Requery и Clear (VBScript) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Execute method [ADO], VBScript example
- Clear method [ADO], VBScript example
- Requery method [ADO], VBScript example
ms.assetid: 3a7bbf07-2fca-4892-95f4-eec93f2d5e91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 27a177b6a3d23f20790490e1f16fac2be4ec958f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918816"
---
# <a name="execute-requery-and-clear-methods-example-vbscript"></a>Пример методов Execute, Requery и Clear (VBScript)
В этом примере демонстрируется метод **EXECUTE** при запуске из объекта [команды](../../../ado/reference/ado-api/command-object-ado.md) и объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) . Он также использует метод [Requery](../../../ado/reference/ado-api/requery-method.md) для получения текущих данных в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md)и метод [clear](../../../ado/reference/ado-api/clear-method-ado.md) для очистки содержимого коллекции [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) . Для выполнения этой процедуры требуются процедуры ExecuteCommand и Принтаутпут.  
  
 Используйте следующий пример на странице Active Server (ASP). Чтобы просмотреть этот полнофункциональный пример, необходимо иметь источник данных Адвворкс. mdb (установленный с примерами пакета SDK), расположенный в папке C:\Program Files\Microsoft Platform Сдк\самплес\датаакцесс\рдс\рдстест\адвворкс.МДБ, или изменить путь в примере кода, чтобы отразить фактическое расположение этого файла. Это файл базы данных Microsoft Access.  
  
 Используйте **Find** для поиска файла адовбс. Inc и поместите его в каталог, который планируется использовать. Вырежьте и вставьте следующий код в Блокнот или другой текстовый редактор и сохраните его как **ексекутевбс. ASP**. Результат можно просмотреть в любом клиентском браузере.  
  
```  
<!-- BeginExecuteVBS -->  
<%@ Language=VBScript %>  
<% ' use this meta tag instead of ADOVBS.inc%>  
<!-- METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4"  -->  
<HTML>  
<HEAD>  
<META name="VI60_DefaultClientScript"  content=VBScript>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<title>ADO Execute Method</title>  
<STYLE>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</STYLE>  
</HEAD>  
  
<BODY>  
<H3>ADO Execute Method</H3>  
<HR>  
<H4>Recordset Retrieved Using Connection Object</H4>  
<!--- Recordsets retrieved using Execute method of Connection and Command Objects-->  
<%   
     ' connection, command and recordset variables  
    Dim Cnxn, strCnxn  
    Dim rsCustomers, strSQLCustomers  
    Dim Cmd   
    Dim rsProducts, strSQLProducts  
  
    ' create and open connection  
    Set Cnxn = Server.CreateObject("ADODB.Connection")   
    strCnxn="Provider='sqloledb';Data Source=" & _  
            Request.ServerVariables("SERVER_NAME") & ";" & _  
            "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    Cnxn.Open  strCnxn  
    ' create and open recordset  
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")  
    strSQLCustomers = "Customers"  
    rsCustomers.Open strSQLCustomers, Cnxn, adOpenKeyset, adLockOptimistic, adCmdTable  
  
    '1st Recordset using Connection - Execute  
    Set rsCustomers = Cnxn.Execute(strSQLCustomers)   
  
    Set Cmd = Server.CreateObject("ADODB.Command")  
    Cmd.ActiveConnection = Cnxn  
    strSQLProducts = "SELECT * From Products"  
    Cmd.CommandText = strSQLProducts  
  
    '2nd Recordset Cmd - execute   
    Set rsProducts = Cmd.Execute  
    %>  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0 ALIGN=CENTER>  
    <!-- BEGIN column header row for Customer Table-->  
    <TR CLASS=thead>  
      <TH>Company Name</TH>  
      <TH>Contact Name</TH>  
      <TH>City</TH>  
    </TR>  
  
    <!--Display ADO Data from Customer Table-->  
    <%   
    Do While Not rsCustomers.EOF %>  
      <TR CLASS=tbody>  
        <TD>   
        <%= rsCustomers("CompanyName")%>   
        </TD>  
        <TD>  
        <%= rsCustomers("ContactName") %>   
        </TD>  
        <TD>   
        <%= rsCustomers("City")%>   
        </TD>  
      </TR>   
      <%   
    rsCustomers.MoveNext   
    Loop   
    %>  
</TABLE>  
  
<HR>  
<H4>Recordset Retrieved Using Command Object</H4>  
  
<TABLE CELLPADDING=5 BORDER=0 ALIGN=CENTER WIDTH="80%">  
  
<!-- BEGIN column header row for Product List Table-->  
<TR CLASS=thead2>  
  <TH>Product Name</TH>  
  <TH>Unit Price</TH>  
</TR>  
  
<!-- Display ADO Data Product List-->  
<% Do Until rsProducts.EOF %>  
  <TR CLASS=tbody>  
    <TD>  
    <%= rsProducts("ProductName")%>    
    </TD>  
    <TD>   
    <%= rsProducts("UnitPrice")%>   
    </TD>  
<%   
    rsProducts.MoveNext   
    Loop  
  
    ' clean up  
    If rsCustomers.State = adStateOpen then  
        rsCustomers.Close  
    End If  
    If rsProducts.State = adStateOpen then  
        rsProducts.Close  
    End If  
    If Cnxn.State = adStateOpen then  
        Cnxn.Close  
    End If  
    Set Cmd = Nothing  
    Set rsCustomers = Nothing  
    Set rsProducts = Nothing  
    Set Cnxn = Nothing  
%>  
</TABLE>  
  
</BODY>  
</HTML>  
<!-- EndExecuteVBS -->  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Объект Error](../../../ado/reference/ado-api/error-object.md)   
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Метод Execute (команда ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Метод Execute (соединение ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Метод Requery](../../../ado/reference/ado-api/requery-method.md)
