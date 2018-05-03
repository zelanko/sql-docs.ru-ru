---
title: Столбцы и таблицы методы добавления, введите имя примера свойства (Visual Basic) | Документы Microsoft
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
- Name property [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: 678e5546-df5d-4cd0-bfe9-6cf13cb385c0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 978b92f3cb4196d766ec2ef7d48b85f37b8c1b67
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="columns-and-tables-append-methods-name-property-example-vb"></a>Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)
Следующий код демонстрирует создание новой таблицы.  
  
```  
' BeginCreateTableVB  
Sub Main()  
    On Error GoTo CreateTableError  
  
    Dim tbl As New Table  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog.  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    tbl.Name = "MyTable"  
    tbl.Columns.Append "Column1", adInteger  
    tbl.Columns.Append "Column2", adInteger  
    tbl.Columns.Append "Column3", adVarWChar, 50  
    cat.Tables.Append tbl  
    Debug.Print "Table 'MyTable' is added."  
  
    'Delete the table as this is a demonstration.  
    cat.Tables.Delete tbl.Name  
    Debug.Print "Table 'MyTable' is deleted."  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set tbl = Nothing  
    Exit Sub  
  
CreateTableError:  
  
    Set cat = Nothing  
    Set tbl = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateTableVB  
```  
  
## <a name="see-also"></a>См. также  
 [Append-метод (ADOX столбцы)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-метод (ADOX таблицы)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Объект столбца (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Коллекция столбцов (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [Объект таблицы (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)
