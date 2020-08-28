---
description: Примеры метода Append коллекции Keys, свойства Type объекта Key, а также примеры свойств RelatedColumn, RelatedTable и UpdateRule (Visual Basic)
title: Пример создания связи по внешнему ключу между таблицами (Visual Basic) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Key Type property [ADOX], Visual Basic example
- RelatedTable property [ADOX], Visual Basic example
- Keys Append method [ADOX], Visual Basic example
- UpdateRule property [ADOX], Visual Basic example
- RelatedColumn property [ADOX], Visual Basic example
ms.assetid: 13b5b1c3-6af6-439e-bb65-976578ba6bc2
author: rothja
ms.author: jroth
ms.openlocfilehash: edc38c1506e472eddb6640c9d7ca121154dcc4cb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984065"
---
# <a name="keys-append-method-key-type-relatedcolumn-relatedtable-and-updaterule-properties-example-vb"></a>Примеры метода Append коллекции Keys, свойства Type объекта Key, а также примеры свойств RelatedColumn, RelatedTable и UpdateRule (Visual Basic)
В следующем коде показано, как создать связь по внешнему ключу между двумя существующими таблицами с именами **Customers** и **Orders**.  
  
```  
' BeginCreateKeyVB  
Sub Main()  
    On Error GoTo CreateKeyError  
  
    Dim kyForeign As New ADOX.Key  
    Dim cat As New ADOX.Catalog  
  
    ' Connect to the catalog.  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Define the foreign key.  
    kyForeign.Name = "CustOrder"  
    kyForeign.Type = adKeyForeign  
    kyForeign.RelatedTable = "Customers"  
    kyForeign.Columns.Append "CustomerId"  
    kyForeign.Columns("CustomerId").RelatedColumn = "CustomerId"  
    kyForeign.UpdateRule = adRICascade  
  
    ' Append the foreign key to the keys collection.  
    cat.Tables("Orders").Keys.Append kyForeign  
  
    'Delete the key t demonstrate the Delete method.  
    cat.Tables("Orders").Keys.Delete kyForeign.Name  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set kyForeign = Nothing  
    Exit Sub  
  
CreateKeyError:  
    Set cat = Nothing  
    Set kyForeign = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndCreateKeyVB  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (ключи ADOX)](./append-method-adox-keys.md)   
 [Объект каталога (ADOX)](./catalog-object-adox.md)   
 [Объект Column (ADOX)](./column-object-adox.md)   
 [Коллекция Columns (ADOX)](./columns-collection-adox.md)   
 [Ключевой объект (ADOX)](./key-object-adox.md)   
 [Коллекция Keys (ADOX)](./keys-collection-adox.md)   
 [Свойство Name (ADOX)](./name-property-adox.md)   
 [Свойство RelatedColumn (ADOX)](./relatedcolumn-property-adox.md)   
 [Свойство RelatedTable (ADOX)](./relatedtable-property-adox.md)   
 [Объект Table (ADOX)](./table-object-adox.md)   
 [Коллекция Tables (ADOX)](./tables-collection-adox.md)   
 [Свойство Type (Key) (ADOX)](./type-property-key-adox.md)   
 [Свойство UpdateRule (ADOX)](./updaterule-property-adox.md)