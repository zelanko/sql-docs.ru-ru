---
title: Учебник по RDS (VBScript) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a50b9d8c1f22f23f3533240b2543ef981fef8e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931378"
---
# <a name="rds-tutorial-vbscript"></a>Учебник по RDS (VBScript)
Это учебник по RDS, написанных на Visual Basic Scripting Edition. Описание цели этого руководства, см. в разделе [учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В этом руководстве [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) и [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) создаются во время разработки — то есть они определяются с помощью теги объектов, следующим образом: `<OBJECT>...</OBJECT>`. В качестве альтернативы они могут создаваться во время выполнения с [метод CreateObject (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md) метод. Например **RDS. DataControl** может быть создан следующим образом:  
  
```vb
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
  
## <a name="step-1---specify-a-server-program"></a>Шаг 1 — укажите программу сервера  
 VBScript можно обнаружить имя веб-сервера IIS он выполняется, обратившись к VBScript **Request.ServerVariables** доступный метод для ASP-страницы:  
  
```vb
"https://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Тем не менее для этого руководства используйте мнимой сервера «сервер».  
  
> [!NOTE]
>  Обратите внимание на тип данных **ByRef** аргументы. VBScript не позволяет указать тип переменной, поэтому всегда необходимо передать **Variant**. При использовании протокола HTTP, RDS позволит вам для передачи Variant метод, который ожидает, что если вызывается с не Variant **RDS. Пространство данных** объект [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) метод. При использовании DCOM или сервере в процессе, вы должны совпадать с типами параметров на клиентской и серверной сторон или появится сообщение об ошибке «Несоответствие типов».  
  
```vb
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "https://yourServer")  
```  
  
## <a name="step-2a---invoke-the-server-program-with-rdsdatacontrol"></a>Шаг 2а - вызовите программу сервера с помощью RDS. DataControl  
 В этом примере является просто комментарием, демонстрируя, что по умолчанию **RDS. DataControl** — выполнить указанный запрос.  
  
```vb
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="https://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial2A()  
   Dim RS  
   DC1.Refresh  
   Set RS = DC1.Recordset  
...  
```  
  
## <a name="step-2b---invoke-the-server-program-with-rdsserverdatafactory"></a>Шаг 2b - вызовите программу сервера с RDSServer.DataFactory  
  
## <a name="step-3---server-obtains-a-recordset"></a>Шаг 3 - сервер получает набор записей  
  
## <a name="step-4---server-returns-the-recordset"></a>Шаг 4 - сервер возвращает набор записей  
  
```vb
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5---datacontrol-is-made-usable-by-visual-controls"></a>Шаг 5 - DataControl обеспечивается можно использовать визуальные элементы управления  
  
```vb
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a---changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Шаг 6а. изменения отправляются на сервер с помощью RDS. DataControl  
 В этом примере является просто комментарием Демонстрация как **RDS. DataControl** выполняет обновление.  
  
```vb
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="https://yourServer/">  
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
  
## <a name="step-6b---changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Шаге 6б. изменения будут отправлены на сервер с RDSServer.DataFactory  
  
```vb
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Это происходит в конце этого руководства.**  
  
## <a name="see-also"></a>См. также  
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
