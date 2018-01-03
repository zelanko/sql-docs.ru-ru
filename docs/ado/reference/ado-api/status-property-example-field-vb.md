---
title: "Пример свойства состояния (поле) (Visual Basic) | Документы Microsoft"
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
helpviewer_keywords: Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e1abe338e6034fec34d1576b52af6df43970ea9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="status-property-example-field-vb"></a>Пример свойства состояния (поле) (Visual Basic)
В следующем примере открывается документ из папки/Чтение с помощью [публикации поставщика услуг Интернета](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). [Состояние](../../../ado/reference/ado-api/status-property-ado-field.md) свойство [поле](../../../ado/reference/ado-api/field-object.md) объект [запись](../../../ado/reference/ado-api/record-object-ado.md) сначала устанавливается **adFieldPendingInsert**, обновляться для **adFieldOk**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=http://MyServer/"  
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
  
 В следующем примере удаляется известный **поле** из **записи** открывается из документа. **Состояние** сначала присваивается свойству **adFieldOK**, затем **adFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 В следующем примере кода удаляет **поле** из **записи** открыт только для чтения документа. **Состояние** будет присвоено **adFieldPendingDelete**. В [обновление](../../../ado/reference/ado-api/update-method.md), удаление завершится ошибкой и **состояние** будет **adFieldPendingDelete** , а также **adFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) очищает отложенные **состояние** параметр.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект field](../../../ado/reference/ado-api/field-object.md)   
 [Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Свойство Status (объект Field ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
