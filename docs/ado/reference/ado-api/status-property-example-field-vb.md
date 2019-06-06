---
title: Пример свойства Status (объект Field) (Visual Basic) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 12ae39b965678a47053d3d312c750f7bd87bd7d1
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719052"
---
# <a name="status-property-example-field-vb"></a>Пример свойства Status (объект Field) (Visual Basic)
В следующем примере открывается документ из папки чтения и записи с помощью [публикации поставщик Интернета](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). [Состояние](../../../ado/reference/ado-api/status-property-ado-field.md) свойство [поле](../../../ado/reference/ado-api/field-object.md) объект [записи](../../../ado/reference/ado-api/record-object-ado.md) сначала будет указано значение **adFieldPendingInsert**, обновляться для **adFieldOk**.  
  
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
  
 В следующем примере удаляется известная **поле** из **записи** открывается из документа. **Состояние** сначала присваивается свойству **adFieldOK**, затем **adFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Следующий код удаляет **поле** из **записи** открывается на документ только для чтения. **Состояние** будет присвоено **adFieldPendingDelete**. В [обновление](../../../ado/reference/ado-api/update-method.md), удаление завершится ошибкой и **состояние** будет **adFieldPendingDelete** , а также **adFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) очищает отложенные **состояние** параметр.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>См. также  
 [Объект field](../../../ado/reference/ado-api/field-object.md)   
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Свойство Status (объект Field ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
