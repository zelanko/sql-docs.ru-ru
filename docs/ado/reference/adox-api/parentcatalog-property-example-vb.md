---
title: Пример свойства ParentCatalog (Visual Basic) | Документация Майкрософт
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
- ParentCatalog property [ADOX], Visual Basic example
ms.assetid: 448bc850-7584-4c5f-89f3-5f4fee88b259
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f87a092d20fb15a23e21a7ef9f0094e40eedeb57
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965595"
---
# <a name="parentcatalog-property-example-vb"></a>Пример свойства ParentCatalog (Visual Basic)
В следующем коде показано, как использовать свойство [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) для доступа к свойству, зависящему от поставщика, до добавления таблицы в каталог. Свойство имеет значение **AutoIncrement**, которое создает поле автоприращения в базе данных Microsoft Jet.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Метод Append (столбцы ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Метод Append (таблицы ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Коллекция Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [Свойство ParentCatalog (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md)   
 [Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Свойство Type (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
