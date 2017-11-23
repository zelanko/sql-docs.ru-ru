---
title: "Пример свойства состояние готовности (VBScript) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords: ReadyState property [ADO], VBScript example
ms.assetid: e3e18da4-0511-4ece-a35d-699978bc28c6
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a3cc3f3ecd687b0a00054e8fd82c24e83d9f7ea6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="readystate-property-example-vbscript"></a>Пример свойства состояние готовности (VBScript)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В следующем примере показано, как прочитать [состояние готовности](../../../ado/reference/rds-api/readystate-property-rds.md) свойство [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта во время выполнения в код VBScript. **Состояние готовности** доступно только для чтения.  
  
 Чтобы протестировать этот пример, вырежьте и вставьте следующий код между \<Body > и \</Body > тегов в обычный HTML документа и назовите его **RDSReadySt.asp**. Используйте **найти** для нахождения файла Adovbs.inc и поместите его в каталог, который планируется использовать. Сценарий ASP будет идентификации сервера.  
  
```  
<!-- BeginReadyStateVBS -->  
<%@ Language=VBScript %>  
<!--#include file="adovbs.inc"-->  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>RDS.DataControl ReadyState Property</title>  
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
<H1>RDS.DataControl ReadyState Property</H1>  
<H2>RDS API Code Examples </H2>  
<HR>  
<!-- RDS.DataControl with parameters set at design time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS>  
   <PARAM NAME="SQL" VALUE="Select * from Orders">  
   <PARAM NAME="SERVER" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=SQLOLEDB;Integrated Security=SSPI;Initial Catalog=Northwind">  
   <PARAM NAME="ExecuteOptions" VALUE="2">   
   <PARAM NAME="FetchOptions" VALUE="3">  
</OBJECT>  
  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="OrderID"></SPAN></TD>  
  </TR>  
</TBODY>  
</TABLE>  
  
<Script Language="VBScript">  
  
   Sub Window_OnLoad  
  
      Select Case RDS.ReadyState  
         case 2   'adcReadyStateLoaded  
          MsgBox "Executing Query"  
         case 3   'adcReadyStateInteractive  
          MsgBox "Fetching records in background"  
         case 4   'adcReadyStateComplete  
          MsgBox "All records fetched"  
      End Select  
  
   End Sub  
</Script>  
  
</body>  
</html>  
<!-- EndReadyStateVBS -->  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Свойство ReadyState (служба удаленных рабочих столов)](../../../ado/reference/rds-api/readystate-property-rds.md)


