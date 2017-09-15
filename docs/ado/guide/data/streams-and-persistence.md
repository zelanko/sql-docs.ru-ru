---
title: "Потоки и сохраняемость | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisted streams [ADO]
- streams [ADO], persistence
ms.assetid: ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: af1ecf7ed9f4702d986d6f1881b3264ab8171c87
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="streams-and-persistence"></a>Потоки и сохраняемости
[Записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта [Сохранить](../../../ado/reference/ado-api/save-method.md) метод хранилища, или *сохраняется*, **записей** в файле и [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md)восстановление метод **записей** из этого файла.  
  
 При использовании ADO 2.7 или более поздней версии **Сохранить** и **откройте** сохраняющую методы **набора записей** для [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекта также. Эта возможность особенно полезна при работе с удаленной службе данных (RDS) и Active Server Pages (ASP).  
  
 Дополнительные сведения об использовании сохраняемости в сам по себе на ASP-страниц см. в текущей документации ASP.  
  
 Ниже приведены несколько сценариев, которые показывают, как **поток** можно использовать объекты и сохраняемость.  
  
## <a name="scenario-1"></a>Сценарий 1  
 Этот сценарий просто сохраняет **записей** в файл, а затем в **поток**. После этого он открывает постоянного потока в другой **записей**.  
  
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
 Этот сценарий будет повторяться **записей** в **поток** в формате XML. Затем считывает **поток** в строку, которую можно проверить, манипуляции или отображения.  
  
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
 В этом примере кода показано сохранение кода ASP **записей** как XML-Документы, непосредственно **ответ** объекта:  
  
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
  
## <a name="scenario-4"></a>Сценарий 4.  
 В этом сценарии ASP-код записывает содержимое **записей** в формате ADTG клиенту. [Службы курсора для OLE DB Microsoft](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) эти данные можно использовать для создания несвязанный **записей**.  
  
 Новое свойство для служб удаленных рабочих СТОЛОВ [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md), [URL-адрес](../../../ado/reference/rds-api/url-property-rds.md), указывает на страницу .asp, приводит к возникновению ошибки **записей**. Это означает **записей** можно получить объект без служб удаленных рабочих СТОЛОВ с помощью сервере [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта или пользователя, Создание бизнес-объекта. Это значительно упрощает модель программирования служб удаленных рабочих СТОЛОВ.  
  
 Серверный код, с именем http://server/directory/recordset.asp:  
  
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
    <PARAM NAME="URL" VALUE="http://server/directory/recordset.asp">  
</OBJECT>  
  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 Разработчики также имеют возможность использования **записей** объекта на стороне клиента:  
  
```  
...  
function GetRs()   
    {  
    rs = CreateObject("ADODB.Recordset");  
    rs.Open "http://server/directory/recordset.asp"  
    DC1.SourceRecordset = rs;  
    }  
...  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Save-метод](../../../ado/reference/ado-api/save-method.md)
