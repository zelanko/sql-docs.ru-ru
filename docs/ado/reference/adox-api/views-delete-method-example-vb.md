---
description: Пример метода Delete коллекции Views (Visual Basic)
title: Пример метода Delete в представлениях (Visual Basic) | Документация Майкрософт
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
- Delete method [ADOX]
ms.assetid: 17df2a83-4166-4df8-8c17-0a33aaac8582
author: rothja
ms.author: jroth
ms.openlocfilehash: 887b558b3bff61a571a2333719164ba3e577782b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439286"
---
# <a name="views-delete-method-example-vb"></a>Пример метода Delete коллекции Views (Visual Basic)
В следующем коде показано, как использовать метод [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) для удаления представления из каталога.  
  
```  
' BeginDeleteViewVB  
Sub Main()  
    On Error GoTo DeleteViewError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    'Delete the View  
    cat.Views.Delete "AllCustomers"  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteViewError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteViewVB  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод Delete (ADOX Collections)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [Коллекция Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
