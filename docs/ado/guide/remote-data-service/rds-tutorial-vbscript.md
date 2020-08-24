---
description: Учебник по RDS (VBScript)
title: Руководство по RDS (VBScript) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c8e93e72833e649f46ebda5885d3a16c5afece6
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759514"
---
# <a name="rds-tutorial-vbscript"></a>Учебник по RDS (VBScript)
Это руководство по RDS, написанное на Microsoft Visual Basic Scripting Edition. Описание назначения этого учебника см. в [руководстве по RDS](./rds-tutorial.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В этом руководстве [RDS. Элемент управления](../../reference/rds-api/datacontrol-object-rds.md) и [RDS. Пространство](../../reference/rds-api/dataspace-object-rds.md) данных создается во время разработки, то есть они определяются с помощью тегов объектов следующим образом: `<OBJECT>...</OBJECT>` . Кроме того, они могут быть созданы во время выполнения с помощью метода [CreateObject (RDS)](../../reference/rds-api/createobject-method-rds.md) . Например, **RDS. Объект элемента управления** данным можно создать следующим образом:  
  
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
  
## <a name="step-1---specify-a-server-program"></a>Шаг 1. Указание серверной программы  
 Сценарий VBScript может обнаружить имя веб-сервера IIS, на котором он работает, обратившись к методу **request. ServerVariables** , доступному для Active Server страниц:  
  
```vb
"https://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Однако в этом руководстве используется мнимой сервер «Йоурсервер».  
  
> [!NOTE]
>  Обратите внимание на тип данных аргументов **ByRef** . VBScript не позволяет указать тип переменной, поэтому всегда необходимо передавать **вариант**. При использовании протокола HTTP RDS позволяет передать вариант в метод, который предполагает, что не является вариантным, если вызвать его с помощью **RDS. ** Метод [CreateObject](../../reference/rds-api/createobject-method-rds.md) объекта пространства на объекте. При использовании DCOM или внутрипроцессного сервера необходимо сопоставить типы параметров на стороне клиента и сервера, иначе вы получите ошибку "несоответствие типов".  
  
```vb
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "https://yourServer")  
```  
  
## <a name="step-2a---invoke-the-server-program-with-rdsdatacontrol"></a>Шаг 2A. вызов серверной программы с помощью RDS. DataControl  
 Этот пример представляет собой просто комментарий, демонстрирующий поведение RDS по умолчанию **. Элемент управления** "данные" предназначен для выполнения указанного запроса.  
  
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
  
## <a name="step-2b---invoke-the-server-program-with-rdsserverdatafactory"></a>Шаг 2b. вызов серверной программы с помощью RDSServer. фактов  
  
## <a name="step-3---server-obtains-a-recordset"></a>Шаг 3. сервер получает набор записей  
  
## <a name="step-4---server-returns-the-recordset"></a>Шаг 4. сервер возвращает набор записей  
  
```vb
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5---datacontrol-is-made-usable-by-visual-controls"></a>Шаг 5. элемент управления "элементы" можно использовать в визуальных элементах управления  
  
```vb
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a---changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Шаг 6a. изменения отправляются на сервер с помощью RDS. DataControl  
 Этот пример представляет собой просто комментарий, демонстрирующий, как **RDS. Элемент управления** "выполнение обновлений" выполняет обновления.  
  
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
  
## <a name="step-6b---changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Шаг 6B. изменения отправляются на сервер с помощью RDSServer.  
  
```vb
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Это последняя часть руководства.**  
  
## <a name="see-also"></a>См. также  
 [Учебник по RDS](./rds-tutorial.md)