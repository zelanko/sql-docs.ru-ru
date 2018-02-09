---
title: "Учебник служб удаленных рабочих СТОЛОВ (VBScript) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70617ccbb2b0b874c68ea45cc72390bd98a52061
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="rds-tutorial-vbscript"></a>Учебник служб удаленных рабочих СТОЛОВ (VBScript)
Это учебник служб удаленных рабочих СТОЛОВ, написанных на Visual Basic Scripting Edition. Описание назначения этого учебника см. в разделе [учебника служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-tutorial.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В этом учебнике [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) и [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) создаются во время разработки, то есть они определяются с помощью тегов объектов, следующим образом: `<OBJECT>...</OBJECT>`. Кроме того, они могут создаваться во время выполнения с [метод CreateObject (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md) метод. Например **RDS. DataControl** может быть создан следующим образом:  
  
```  
Set DC = Server.CreateObject("RDS.DataControl")  
   <!-- RDS.DataControl -->  
   <OBJECT   
      ID="DC1" CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E33">  
   </OBJECT>  
  
   <!-- RDS.DataSpace -->  
   <OBJECT   
      ID="DS1" WIDTH=1 HEIGHT=1  
      CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
   </OBJECT>  
  
   <SCRIPT LANGUAGE="VBScript">  
  
   Sub RDSTutorial()  
   Dim DF1   
```  
  
## <a name="step-1--specify-a-server-program"></a>Шаг 1 — Укажите программу server  
 VBScript можно получить имя веб-сервера IIS его выполнения, обратившись к VBScript **Request.ServerVariables** доступный метод для Active Server Pages:  
  
```  
"http://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Однако в этом учебнике используйте мнимой сервера «сервер».  
  
> [!NOTE]
>  Обратите внимание на тип данных **ByRef** аргументы. VBScript не позволяет указать тип переменной, поэтому всегда необходимо передать **Variant**. При использовании HTTP, служб удаленных рабочих СТОЛОВ позволяет передачи Variant методу, который ожидает типа Variant, если вызвать его с **RDS. Пространство данных** объекта [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) метод. При использовании DCOM или внутрипроцессного сервера, необходимо сопоставить типы параметров на сторонах клиента и сервера или появится сообщение об ошибке «Несоответствие типов».  
  
```  
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "http://yourServer")  
```  
  
## <a name="step-2a--invoke-the-server-program-with-rdsdatacontrol"></a>Шаг 2а — вызвать программу server с RDS. DataControl  
 Данный пример является просто комментарий, демонстрирующий поведение по умолчанию **RDS. DataControl** выполнить указанный запрос.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="http://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial2A()  
   Dim RS  
   DC1.Refresh  
   Set RS = DC1.Recordset  
...  
```  
  
## <a name="step-2b--invoke-the-server-program-with-rdsserverdatafactory"></a>Шаг 2b — вызвать программу server с RDSServer.DataFactory  
  
## <a name="step-3--server-obtains-a-recordset"></a>Шаг 3 — Сервер получает набор записей  
  
## <a name="step-4--server-returns-the-recordset"></a>Шаг 4 — Сервер возвращает набор записей  
  
```  
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5--datacontrol-is-made-usable-by-visual-controls"></a>Шаг 5 — DataControl сделанный можно использовать визуальные элементы управления  
  
```  
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a--changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Шаг 6a — изменения будут отправлены на сервер с RDS. DataControl  
 Данный пример является просто комментарий демонстрации как **RDS. DataControl** выполняет обновление.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="http://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial6A()  
Dim RS  
DC1.Refresh  
...  
Set RS = DC1.Recordset  
' Edit the Recordset object...  
' The SERVER and CONNECT properties are already set from Step 2A.  
Set DC1.SourceRecordset = RS  
...  
DC1.SubmitChanges  
```  
  
## <a name="step-6b--changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Шаг 6b — изменения будут отправлены на сервер с RDSServer.DataFactory  
  
```  
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Это конец учебника.**  
  
## <a name="see-also"></a>См. также  
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
