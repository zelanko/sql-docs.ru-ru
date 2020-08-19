---
description: Потоки и сохраняемость
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 869c5ef7380c315b60d2cbf6ad11f0cf638a0d7f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452776"
---
# <a name="streams-and-persistence"></a>Потоки и сохраняемость
Метод [сохранения](../../../ado/reference/ado-api/save-method.md) объекта [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) сохраняет или сохраняет **набор записей** в *файле, а*метод [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) восстанавливает **набор записей** из этого файла.  
  
 При использовании ADO 2,7 или более поздней версии методы **Save** и **Open** могут также сохранить **набор записей** в объекте [потока](../../../ado/reference/ado-api/stream-object-ado.md) . Эта функция особенно полезна при работе с удаленной службой данных (RDS) и Active Server страницами (ASP).  
  
 Дополнительные сведения о том, как можно использовать сохраняемость на страницах ASP, см. в текущей документации по ASP.  
  
 Ниже приведено несколько сценариев, демонстрирующих, как можно использовать объекты **Stream** и сохраняемость.  
  
## <a name="scenario-1"></a>Сценарий 1  
 Этот сценарий просто сохраняет **набор записей** в файл, а затем в **поток**. Затем он открывает сохраненный поток в другом **наборе записей**.  
  
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
 Этот сценарий сохраняет **набор записей** в **потоке** в формате XML. Затем он считывает **поток** в строку, которую можно просматривать, изменять или отображать.  
  
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
 В этом примере кода показан код ASP, сохраняющий **набор записей** в виде XML непосредственно в объекте **Response** :  
  
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
 В этом сценарии код ASP записывает содержимое **набора записей** в формате адтг клиенту. [Служба курсора Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) может использовать эти данные для создания отключенного **набора записей**.  
  
 Новое свойство в [элементе управления](../../../ado/reference/rds-api/datacontrol-object-rds.md)RDS ( [URL](../../../ado/reference/rds-api/url-property-rds.md)) указывает на страницу. ASP, создающую **набор записей**. Это означает, что объект **набора записей** можно получить без RDS, используя объект [факта](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) на стороне сервера или пользователь, записывающий бизнес-объект. Это значительно упрощает модель программирования RDS.  
  
 Код на стороне сервера с именем https://server/directory/recordset.asp:  
  
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
  
 Разработчики также имеют возможность использовать объект **Recordset** на клиенте:  
  
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
  
## <a name="see-also"></a>См. также:  
 [Метод Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
