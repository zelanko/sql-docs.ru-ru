---
title: Пример метода ConvertToString (VBScript) | Документация Майкрософт
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
- ConvertToString method [ADO], VBScript example
ms.assetid: edd0a01c-1a1b-4b91-9966-2529e244abae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7f1a765d67307eb116c567c9cd5998d27b1ff53
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770122"
---
# <a name="converttostring-method-example-vbscript"></a>Пример метода ConvertToString (VBScript)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В следующем примере показано, как преобразовать **записей** в строку в кодировке MIME, используя **RDSServer.DataFactory ConvertToString** метод. В нем также показано, как можно преобразовать строку обратно в **записей**. Вырежьте и вставьте следующий код в блокноте или другом текстовом редакторе и сохраните его как **ConvertToString.htm**.  
  
```  
<!-- BeginConvertToStringVBS -->  
<HTML>  
<HEAD><TITLE>ConvertToString Example</TITLE><HEAD>  
<BODY>  
  
<SCRIPT LANGUAGE=VBSCRIPT>  
Sub ConvertToStringX()  
    Dim objRs, objDF, strServer, vString  
    Const adcExecSync = 1  
    Const adcFetchUpFront = 1  
  
    ' Replace value below with your server name to use without ASP.  
    strServer = "http://<%=Request.ServerVariables("SERVER_NAME")%>">  
  
    Set objDF = RDS1.CreateObject("RDSServer.DataFactory", strServer)  
    Set objRs = objDF.Query(txtConnect.Value,txtQueryRecordset.Value)  
  
    ' convert Recordset to MIME encoded string  
    vString = objDF.ConvertToString(objRs)  
  
    ' display MIME string for demo purposes  
    txtRS.value = vString  
  
    ' convert MIME string back to useable ADO Recordset   
    ' using RDS.DataControl  
    RDC1.SQL = vString  
  
    RDC1.ExecuteOptions = adcExecSync  
    RDC1.FetchOptions = adcFetchUpFront  
    RDC1.Refresh  
  
    MsgBox "RecordCount = " & RDC1.Recordset.RecordCount  
End Sub   
</SCRIPT>  
  
Connect String:   
 <INPUT TYPE=Text NAME=txtConnect SIZE=50   
    VALUE="Provider=sqloledb;Initial Catalog=pubs;Integrated Security='SSPI';">   
 <BR>  
  
Query:   
 <INPUT TYPE=Text NAME=txtQueryRecordset SIZE=50   
    VALUE="select * from authors">   
 <BR>  
  
 <INPUT TYPE=Button VALUE="ConvertToString" OnClick="ConvertToStringX()">  
 <BR>  
  
MIME Encoded RS: <BR>  
 <TEXTAREA NAME=txtRS ROWS=15 COLS=50 WRAP=virtual></TEXTAREA>  
  
<!-- RDS.DataSpace  ID RDS1 -->  
 <OBJECT ID="RDS1" WIDTH=1 HEIGHT=1  
     CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
 </OBJECT>  
  
<!-- RDS.DataControl ID RDC1 -->  
 <OBJECT ID="RDC1" WIDTH=1 HEIGHT=1   
     CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33">  
 </OBJECT>  
</BODY>  
</HTML>  
<!-- EndConvertToStringVBS -->  
```  
  
## <a name="see-also"></a>См. также  
 [Пример метода ConvertToString (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/converttostring-method-rds.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)




