---
title: Пример объекта DataControl (VBScript) | Документация Майкрософт
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
- DataControl object [ADO], VBScript example
ms.assetid: 4f306a51-d5a4-4785-b426-487639cda164
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7eff8a3a016ad7e0cc6b9f928bef4f16891e8375
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67964417"
---
# <a name="datacontrol-object-example-vbscript"></a>Пример объекта DataControl (VBScript)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ниже показано, как задать [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) параметров на этапе разработки, времени и привязывать их к работы с данными элемента управления. Вырежьте и вставьте следующий код между \<текст > и \</Body > теги в обычном HTML документа и назовите его **DataControlDesignVBS.asp**. Сценарий ASP будет идентификации сервера.  
  
```  
<!-- BeginDataControlDesignVBS -->  
<%@ Language=VBScript %>  
<HTML>  
<HEAD>  
<META name="VI60_DefaultClientScript"  content=VBScript>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<title>RDS DataControl</title>  
  
    <%' local style sheet used for display%>  
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
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Remote Data Service</H3>  
<TABLE DATASRC=#RDS>  
<TBODY>  
   <TR>  
      <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
      <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
   </TR>  
</TBODY>  
</TABLE>  
<!-- Remote Data Service with Parameters set at Design Time -->  
  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDS>  
   <PARAM NAME="SQL" VALUE="Select * from Employees for browse">  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'">  
</OBJECT>  
  
</BODY>  
</HTML>  
<!-- EndDataControlDesignVBS -->  
```  
  
 Приведенный ниже показано, как задать необходимые параметры **RDS. DataControl** во время выполнения. Чтобы протестировать этот пример, вырезать и вставить этот код между \<текст > и \</Body > теги в обычном HTML документа и назовите его **DataControlRuntimeVBS.asp**. Сценарий ASP будет идентификации сервера.  
  
```  
<!-- BeginDataControlRuntimeVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>Data Control Object Example (VBScript)</title>  
  
    <%' local style sheet used for display%>  
<style>  
<!--  
body {  
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
</style>  
</head>  
  
<body>  
<h1>Data Control Object Example (VBScript)</h1>  
  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Remote Data Service Run Time</H3>  
  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="au_lname"></SPAN></TD>  
    <TD><SPAN DATAFLD="au_fname"></SPAN></TD>  
  </TR>  
</TBODY>  
</TABLE>  
<% ' RDS.DataControl with no parameters set at design time %>  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS HEIGHT=1 WIDTH=1></OBJECT>  
  
<FORM name="frmInput">  
<HR>  
<Input Size="70" Name="txtServer" Value="https://<%=Request.ServerVariables("SERVER_NAME")%>"><BR>  
<Input Size="100" Name="txtConnect" Value="Provider='sqloledb';Data Source=<%=Request.ServerVariables("SERVER_NAME")%>;Initial Catalog='Pubs';Integrated Security='SSPI';">  
<BR>  
<Input Size="70" Name="txtSQL" Value="Select * from Authors">  
<HR>  
<INPUT TYPE="BUTTON" NAME="Run" VALUE="Run"><BR>  
<H4>Show grid with these values or change them to see data from another ODBC data source on your server</H4>  
</FORM>  
  
<Script Language="VBScript">  
  
' Set parameters of RDS.DataControl at Run Time  
Sub Run_OnClick  
  
   RDS.Server = document.frmInput.txtServer.Value  
   RDS.Connect = document.frmInput.txtConnect.Value  
   RDS.SQL = document.frmInput.txtSQL.Value  
  
   RDS.Refresh  
  
End Sub  
  
</Script>  
  
</body>  
</html>  
<!-- EndDataControlRuntimeVBS -->  
```  
  
## <a name="see-also"></a>См. также  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)


