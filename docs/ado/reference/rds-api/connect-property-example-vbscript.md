---
title: "Пример свойства (VBScript) подключения | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords: Connect property [ADO], VBScript example
ms.assetid: 06297993-fe72-4446-aa76-3b8bc25444f6
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90d762c67a80459e612acbc5da2e4dde4449012f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="connect-property-example-vbscript"></a>Пример свойства (VBScript) подключения
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Этот код показывает, как задать [Connect](../../../ado/reference/rds-api/connect-property-rds.md) во время разработки:  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="ADC1">  
.  
   <PARAM NAME="SQL" VALUE="Select * from Sales">  
   <PARAM NAME="CONNECT" VALUE="Provider=SQLOLEDB;Integrated Security=SSPI;Initial Catalog=Pubs">  
   <PARAM NAME="Server" VALUE="http://MyWebServer">  
.  
</OBJECT>  
```  
  
 Следующий пример показывает, как задать **Connect** свойства во время выполнения в код VBScript.  
  
 Чтобы протестировать этот пример, вырежьте и вставьте код между \<Body > и \</Body > тегов в обычный HTML документа и назовите его **ConnectVBS.asp**. Сценарий ASP будет идентификации сервера.  
  
```  
<!-- BeginConnectVBS -->  
<%@ Language=VBScript %>  
<HTML>  
<HEAD>  
<title>ADO Connect Property</title>  
  
    <%' local style sheet used for display%>  
<STYLE>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
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
<h1>ADO Connect Property (RDS)</h1>  
  
<HR>  
<H3>Set Connect Property at Run Time</H3>  
  
<% ' RDS.DataControl with no parameters set at design time %>  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS HEIGHT=1 WIDTH=1></OBJECT>  
<% ' Bind table to control for data display  %>  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR class="tbody">  
    <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
    <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
  </TR>  
</TBODY>  
</TABLE>  
<FORM name="frmInput">  
    SERVER: <INPUT Name="txtServer" Size="103" Value="http://<%=Request.ServerVariables("SERVER_NAME")%>"><BR>  
    DATA SOURCE: <INPUT Name="txtDataSource" Size="93" Value="<%=Request.ServerVariables("SERVER_NAME")%>"><BR>  
    CONNECT: <INPUT Name="txtConnect" Size="100"><BR>  
    SQL: <INPUT Name="txtSQL" Size="110" Value="Select FirstName, LastName from Employees">  
    <BR>  
    <INPUT TYPE=BUTTON NAME="Run" VALUE="Run">  
    <h4>  
    To make data grid appear, click 'Run' to see the connect string in text box above.  
    </h4>   
</FORM>  
<Script Language="VBScript">  
  
    ' Set parameters of RDS.DataControl at Run Time  
    Sub Run_OnClick  
  
        Dim Cnxn  
            ' build connection string  
        Cnxn = "Provider='sqloledb';"  
        Cnxn = Cnxn & "Data Source="  
        Cnxn = Cnxn & document.frmInput.txtDataSource.value & ";"  
        Cnxn = Cnxn & "Initial Catalog='Northwind';"  
        Cnxn = Cnxn & "Integrated Security='SSPI';"  
            ' assign the value  
        document.frmInput.txtConnect.value = Cnxn  
        MsgBox "Here we go!"  
            ' set RDS properties  
        RDS.Server = document.frmInput.txtServer.value  
        RDS.SQL = document.frmInput.txtSQL.value  
        RDS.Connect = document.frmInput.txtConnect.value  
        RDS.Refresh  
  
    End Sub  
  
</Script>  
  
</BODY>  
</HTML>  
<!-- EndConnectVBS -->  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойство Connect (служба удаленных рабочих столов)](../../../ado/reference/rds-api/connect-property-rds.md)





















