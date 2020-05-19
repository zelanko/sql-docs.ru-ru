---
title: Пример метода Delete процедур (Visual Basic) | Документация Майкрософт
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
- Delete method [ADOX], Visual Basic example
ms.assetid: 94f1ac93-e778-4a40-a85e-94bce5316ac7
author: rothja
ms.author: jroth
ms.openlocfilehash: d270dbc8bc14ba0ce5fdde9a5c964117856e8f51
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748639"
---
# <a name="procedures-delete-method-example-vb"></a>Пример метода Delete коллекции Procedures (Visual Basic)
В следующем коде показано, как удалить процедуру с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) в коллекции [процедур](../../../ado/reference/adox-api/procedures-collection-adox.md) .  
  
```  
' BeginDeleteProcedureVB  
Sub Main()  
    On Error GoTo DeleteProcedureError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Delete the procedure.  
    cat.Procedures.Delete "CustomerById"  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteProcedureError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteProcedureVB  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Метод Delete (ADOX Collections)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [Объект процедуры (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
