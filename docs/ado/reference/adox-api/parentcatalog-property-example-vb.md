---
description: Пример свойства ParentCatalog (Visual Basic)
title: Пример свойства ParentCatalog (Visual Basic) | Документация Майкрософт
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
- ParentCatalog property [ADOX], Visual Basic example
ms.assetid: 448bc850-7584-4c5f-89f3-5f4fee88b259
author: rothja
ms.author: jroth
ms.openlocfilehash: 6910ac229d309360676f83f855664ab368459ce0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983825"
---
# <a name="parentcatalog-property-example-vb"></a>Пример свойства ParentCatalog (Visual Basic)
В следующем коде показано, как использовать свойство [ParentCatalog](./parentcatalog-property-adox.md) для доступа к свойству, зависящему от поставщика, до добавления таблицы в каталог. Свойство имеет значение **AutoIncrement**, которое создает поле автоприращения в базе данных Microsoft Jet.  
  
```  
' BeginCreateAutoIncrColumnVB  
Sub Main()  
    On Error GoTo CreateAutoIncrColumnError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As New ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
  
    With tbl  
        .Name = "MyContacts"  
        Set .ParentCatalog = cat  
        ' Create fields and append them to the new Table object.  
        .Columns.Append "ContactId", adInteger  
        ' Make the ContactId column and auto incrementing column  
        .Columns("ContactId").Properties("AutoIncrement") = True  
        .Columns.Append "CustomerID", adVarWChar  
        .Columns.Append "FirstName", adVarWChar  
        .Columns.Append "LastName", adVarWChar  
        .Columns.Append "Phone", adVarWChar, 20  
        .Columns.Append "Notes", adLongVarWChar  
    End With  
  
    cat.Tables.Append tbl  
    Debug.Print "Table 'MyContacts' is added."  
  
    ' Delete the table as this is a demonstration.  
    cat.Tables.Delete tbl.Name  
    Debug.Print "Table 'MyContacts' is delete."  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set tbl = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CreateAutoIncrColumnError:  
  
    Set cat = Nothing  
    Set tbl = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndCreateAutoIncrColumnVB  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Append (столбцы ADOX)](./append-method-adox-columns.md)   
 [Метод Append (таблицы ADOX)](./append-method-adox-tables.md)   
 [Объект каталога (ADOX)](./catalog-object-adox.md)   
 [Объект Column (ADOX)](./column-object-adox.md)   
 [Коллекция Columns (ADOX)](./columns-collection-adox.md)   
 [Свойство Name (ADOX)](./name-property-adox.md)   
 [Свойство ParentCatalog (ADOX)](./parentcatalog-property-adox.md)   
 [Объект Table (ADOX)](./table-object-adox.md)   
 [Свойство Type (Column) (ADOX)](./type-property-column-adox.md)