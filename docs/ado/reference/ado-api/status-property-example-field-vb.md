---
description: Пример свойства Status (объект Field) (Visual Basic)
title: Пример свойства Status (поле) (VB) | Документация Майкрософт
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
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 148deaa16746bd964e4bed07ed673fea0ec4cb6a
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777293"
---
# <a name="status-property-example-field-vb"></a>Пример свойства Status (объект Field) (Visual Basic)
В следующем примере документ открывается из папки для чтения и записи с помощью [поставщика публикации в Интернете](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Для свойства [Status](./status-property-ado-field.md) объекта [поля](./field-object.md) [записи](./record-object-ado.md) сначала будет задано значение **адфиелдпендингинсерт**, а затем оно будет обновлено на **адфиелдок**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 В следующем примере известное **поле** удаляется из **записи** , открытой из документа. Для свойства **Status** сначала будет задано значение **адфиелдок**, а затем **адфиелдпендингункновн**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Следующий код удаляет **поле** из **записи** , открытой в документе, доступном только для чтения. Для параметра **Status** будет задано значение **адфиелдпендингделете**. Во время [обновления](./update-method.md)удаление завершится ошибкой и **Status** будет отображаться состояние **адфиелдпендингделете** Plus **адфиелдпермиссиондениед**. [CancelUpdate](./cancelupdate-method-ado.md) очищает параметр **состояния** "ожидание".  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Field](./field-object.md)   
 [Объект Record (ADO)](./record-object-ado.md)   
 [Свойство Status (объект Field ADO)](./status-property-ado-field.md)