---
title: Пример свойства объекта ошибки (VB) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Number property [ADO], Visual Basic example
- Source property [ADO], Visual Basic example
- NativeError property [ADO], Visual Basic example
- Description property [ADO], Visual Basic example
- HelpFile property [ADO], Visual Basic example
- SQLState property [ADO], Visual Basic example
- HelpContext property [ADO], Visual Basic example
ms.assetid: 5c728458-d85c-497c-afcf-2cfa36c3342a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6fffa60c8f544435547bfb1e8b940357a0bb4b0
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="description-helpcontext-helpfile-nativeerror-number-source-and-sqlstate-properties-example-vb"></a>Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)
Этот пример вызывает ошибку, он перехватывает и отображает [описание](../../../ado/reference/ado-api/description-property.md), [HelpContext](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md), [HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md), [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md), [ Номер](../../../ado/reference/ado-api/number-property-ado.md), [источника](../../../ado/reference/ado-api/source-property-ado-error.md), и [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) свойства результирующего [ошибка](../../../ado/reference/ado-api/error-object.md) объекта.  
  
```  
'BeginDescriptionVB  
Public Sub Main()  
  
    Dim Cnxn As ADODB.Connection  
    Dim Err As ADODB.Error  
    Dim strError As String  
  
    On Error GoTo ErrorHandler  
  
    ' Intentionally trigger an error  
    Set Cnxn = New ADODB.Connection  
    Cnxn.Open "nothing"  
  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
  
    ' Enumerate Errors collection and display  
    ' properties of each Error object  
    For Each Err In Cnxn.Errors  
        strError = "Error #" & Err.Number & vbCr & _  
            "   " & Err.Description & vbCr & _  
            "   (Source: " & Err.Source & ")" & vbCr & _  
            "   (SQL State: " & Err.SQLState & ")" & vbCr & _  
            "   (NativeError: " & Err.NativeError & ")" & vbCr  
        If Err.HelpFile = "" Then  
            strError = strError & "   No Help file available"  
        Else  
            strError = strError & _  
               "   (HelpFile: " & Err.HelpFile & ")" & vbCr & _  
               "   (HelpContext: " & Err.HelpContext & ")" & _  
               vbCr & vbCr  
        End If  
  
        Debug.Print strError  
    Next  
  
    Resume Next  
End Sub  
'EndDescriptionVB  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Объект Error](../../../ado/reference/ado-api/error-object.md)   
 [HelpContext HelpFile свойства](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [HelpContext HelpFile свойства](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство NativeError (ADO)](../../../ado/reference/ado-api/nativeerror-property-ado.md)   
 [Свойство номера (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (ошибка)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Свойство SQLState](../../../ado/reference/ado-api/sqlstate-property.md)
