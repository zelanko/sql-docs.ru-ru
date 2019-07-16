---
title: Пример метода (Visual Basic) Refresh коллекции Procedures | Документация Майкрософт
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
- Refresh method [ADOX], Visual Basic example
ms.assetid: 499679bd-287b-487d-bdfb-3803abffec1c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9b5201be26bfd9df41c9cb1d8908f59499520878
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965379"
---
# <a name="procedures-refresh-method-example-vb"></a>Пример метода Refresh коллекции Procedures (Visual Basic)
Ниже показано, как обновить [процедуры](../../../ado/reference/adox-api/procedures-collection-adox.md) коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md). Это необходимо перед [процедуры](../../../ado/reference/adox-api/procedure-object-adox.md) объектов из **каталога** возможен.  
  
```  
' BeginProceduresRefreshVB  
Sub Main()  
    On Error GoTo ProcedureRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection  
    cat.Procedures.Refresh  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureRefreshError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndProceduresRefreshVB  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Метод Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
