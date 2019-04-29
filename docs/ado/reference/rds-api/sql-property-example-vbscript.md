---
title: Пример свойства SQL (VBScript) | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- SQL property [ADO], VBScript example
ms.assetid: 32c33bcf-3320-4836-9e2e-99c8978ce581
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcfc53b0882702e5efbb53b8f88bdfb184f86df6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065087"
---
# <a name="sql-property-example-vbscript"></a>Пример свойства SQL (VBScript)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ниже показано, как задать [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) параметр SQL во время разработки и привязки его к элементу управления данными, с помощью базы данных называется *Pubs*, который поставляется с Microsoft SQL Server. Чтобы протестировать пример, скопируйте следующий код в обычном ASP документ с именем **SQLDesignVBS.asp** веб-сервера.  
  
```  
<!-- BeginSQLDesignVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>SQL Property Example (VBScript)</title>  
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
<h1>SQL Property Example (VBScript)</h1>  
  
<!-- RDS.DataControl -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDC HEIGHT=1 WIDTH=1>  
   <PARAM NAME="SQL" VALUE="Select FirstName, LastName from Employees">  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider='sqloledb';Initial Catalog='Northwind';Integrated Security='SSPI';">  
</OBJECT>  
  
<!-- Data Table -->  
  
<TABLE DATASRC=#RDC BORDER=1>  
   <TR>  
      <TD> <SPAN DATAFLD="FirstName"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="LastName"></SPAN> </TD>  
   </TR>  
</TABLE>  
  
</body>  
</html>  
<!-- EndSQLDesignVBS -->  
```  
  
 Приведенный ниже показано, как задать необходимые параметры **RDS. DataControl** во время выполнения. Чтобы протестировать этот пример, вырезать и вставить следующий код в обычном документ ASP и назовите его **SQLRuntimeVBS.asp**. Сценарий ASP будет идентификации сервера.  
  
```  
<!-- BeginSQLRuntimeVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>SQL Property Example (VBScript)</title>  
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
<h1>SQL Property Example (VBScript)</h1>  
  
<H2>RDS API Code Examples </H2>  
<H3>Remote Data Service SQL Property Set at Run Time</H3>  
  
<!-- RDS.DataControl with no parameters set at design time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDC HEIGHT=1 WIDTH=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDC>  
   <TR>  
      <TD> <SPAN DATAFLD="FirstName"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="LastName"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="Title"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="Type"></SPAN> </TD>  
      <TD> <SPAN DATAFLD="Email"></SPAN> </TD>  
   </TR>  
</TABLE>  
  
<HR>  
<Input Size=70 Name="txtServer" Value= "https://<%=Request.ServerVariables("SERVER_NAME")%>">  
<BR>  
<Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';">  
<BR>  
<Input Size=70 Name="txtSQL" VALUE="Select * from Employees">  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run"><BR>  
  
<Script Language="VBScript">  
<!--  
' Set parameters of RDS.DataControl at Run Time.  
Sub Run_OnClick  
   RDC.Server = txtServer.Value  
   RDC.SQL = txtSQL.Value  
   RDC.Connect = txtConnect.Value  
   RDC.Refresh  
End Sub  
-->  
</Script>  
  
</body>  
</html>  
<!-- EndSQLRuntimeVBS -->  
```  
  
## <a name="see-also"></a>См. также  
 [Объект DataControl (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Свойство SQL](../../../ado/reference/rds-api/sql-property.md)



