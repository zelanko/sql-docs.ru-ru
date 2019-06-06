---
title: Потоки и сохраняемость | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisted streams [ADO]
- streams [ADO], persistence
ms.assetid: ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 246d894ff38cc0dd74e96bb0fcbdb7b170b51d53
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700495"
---
# <a name="streams-and-persistence"></a>Потоки и сохраняемость
[Записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект [Сохранить](../../../ado/reference/ado-api/save-method.md) метод хранилищ, или *сохраняется*, **записей** в файле и [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md)метод восстанавливает **записей** из этого файла.  
  
 С помощью ADO 2.7 или более поздней версии **Сохранить** и **откройте** методы можно сохранить **набор записей** для [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объект. Эта функция особенно полезна при работе с удаленной службе данных (RDS) и Active Server Pages (ASP).  
  
 Дополнительные сведения об использовании сохраняемости в сам по себе на ASP-страницах см. в разделе текущей документации ASP.  
  
 Ниже приведены несколько сценариев, которые показывают, как **Stream** объектов и сохранения может использоваться.  
  
## <a name="scenario-1"></a>Сценарий 1  
 Этот сценарий просто сохраняет **записей** в файл, а затем к **Stream**. После этого он открывает постоянного потока в другой **записей**.  
  
```  
Dim rs1 As ADODB.Recordset  
Dim rs2 As ADODB.Recordset  
Dim stm As ADODB.Stream  
  
Set rs1 = New ADODB.Recordset  
Set rs2 = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
rs1.Open   "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;""", adopenStatic, adLockReadOnly, adCmdText  
rs1.Save "c:\myfolder\mysubfolder\myrs.xml", adPersistXML  
rs1.Save stm, adPersistXML  
rs2.Open stm  
```  
  
## <a name="scenario-2"></a>Сценарий 2  
 Этот сценарий будет повторяться **записей** в **Stream** в формате XML. Затем он считывает **Stream** в строку, которая проверки, обработки или отображения.  
  
```  
Dim rs As ADODB.Recordset  
Dim stm As ADODB.Stream  
Dim strRst As String  
  
Set rs = New ADODB.Recordset  
Set stm = New ADODB.Stream  
  
' Open, save, and close the recordset.   
rs.Open "SELECT * FROM Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
rs.Save stm, adPersistXML  
rs.Close  
Set rs = nothing  
  
' Put saved Recordset into a string variable.  
strRst = stm.ReadText(adReadAll)  
  
' Examine, manipulate, or display the XML data.  
...  
```  
  
## <a name="scenario-3"></a>Сценарий 3  
 В этом примере кода показано сохранение кода ASP **записей** как XML непосредственно к **ответа** объекта:  
  
```  
...  
<%  
response.ContentType = "text/xml"  
  
' Create and open a Recordset.  
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select * from Customers", "Provider=sqloledb;" & _  
        "Data Source=MyServer;Initial Catalog=Northwind;" & _  
        "Integrated Security=SSPI;"""  
  
' Save Recordset directly into output stream.  
rs.Save Response, adPersistXML   
  
' Close Recordset.  
rs.Close  
Set rs = nothing  
%>  
...  
```  
  
## <a name="scenario-4"></a>Сценарий 4  
 В этом случае код ASP записывает содержимое **записей** в формате ADTG клиенту. [Служба курсора Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) эти данные можно использовать для создания отключенного **записей**.  
  
 Новое свойство в RDS [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md), [URL-адрес](../../../ado/reference/rds-api/url-property-rds.md), указывает на страницу .asp, который создает **записей**. Это означает, что **записей** может быть получен без служб удаленных рабочих СТОЛОВ на стороне сервера [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта или пользователь, написание бизнес-объекта. Это значительно упрощает модель программирования служб удаленных рабочих СТОЛОВ.  
  
 Код на стороне сервера, с именем https://server/directory/recordset.asp:  
  
```  
<%  
Dim rs   
Set rs = Server.CreateObject("ADODB.Recordset")  
rs.Open "select au_fname, au_lname, phone from Authors", ""& _  
        "Provider=sqloledb;Data Source=MyServer;" & _  
        "Initial Catalog=Pubs;Integrated Security=SSPI;"  
response.ContentType = "multipart/mixed"  
rs.Save response, adPersistADTG  
%>  
```  
  
 Код на стороне клиента:  
  
```  
<HTML>  
<HEAD>  
<TITLE>RDS Query Page</TITLE>  
</HEAD>  
<body>  
<CENTER>  
<H1>Remote Data Service 2.5</H1>  
<TABLE DATASRC="#DC1">  
   <TR>   
      <TD><SPAN DATAFLD="au_fname"></SPAN></TD>  
      <TD><SPAN DATAFLD="au_lname"></SPAN></TD>  
      <TD><SPAN DATAFLD="phone"></SPAN></TD>  
   </TR>  
</TABLE>  
<BR>  
  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
    ID=DC1 HEIGHT=1 WIDTH = 1>  
    <PARAM NAME="URL" VALUE="https://server/directory/recordset.asp">  
</OBJECT>  
  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 Разработчики также имеют возможность использовать **записей** объекта на стороне клиента:  
  
```  
...  
function GetRs()   
    {  
    rs = CreateObject("ADODB.Recordset");  
    rs.Open "https://server/directory/recordset.asp"  
    DC1.SourceRecordset = rs;  
    }  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
