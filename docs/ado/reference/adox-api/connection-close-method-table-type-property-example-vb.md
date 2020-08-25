---
description: Примеры метода Close для объекта Connection и свойства Type для объекта Table (Visual Basic)
title: Метод Close соединения, пример свойства типа таблицы (Visual Basic) | Документация Майкрософт
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
- Close method [ADOX], Visual Basic example
- Type property [ADOX], Visual Basic example
ms.assetid: f88e7a3b-19ed-46e2-b2ce-3b611d9b8166
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b651389b4badd57e6a76b3b38c47c34cc814706
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770913"
---
# <a name="connection-close-method-table-type-property-example-vb"></a>Примеры метода Close для объекта Connection и свойства Type для объекта Table (Visual Basic)
Если задать для свойства [ActiveConnection](./activeconnection-property-adox.md) значение **Nothing** , соединение с каталогом должно быть закрыто. Связанные коллекции будут пустыми. Все объекты, созданные из объектов схемы в каталоге, будут потеряны. Все свойства этих объектов, которые были кэшированы, будут по-прежнему доступны, но попытка чтения свойств, требующих вызова поставщика, завершится ошибкой.  
  
```  
' BeginCloseConnectionVB  
Sub Main()  
    On Error GoTo CloseConnectionByNothingError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Set tbl = cat.Tables(0)  
    Debug.Print tbl.Type    ' Cache tbl.Type info  
    Set cat.ActiveConnection = Nothing  
    Debug.Print tbl.Type    ' tbl is orphaned  
    ' Previous line will succeed if this info was cached.  
    Debug.Print tbl.Columns(0).DefinedSize  
    ' Previous line will fail if this info has not been cached.  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CloseConnectionByNothingError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCloseConnectionVB  
```  
  
 Закрытие объекта [соединения](../ado-api/connection-object-ado.md) , который использовался для открытия каталога, должно иметь тот же результат, что и установка свойства **ActiveConnection** в значение **Nothing**.  
  
```  
Attribute VB_Name = "Connection"  
```  
  
## <a name="see-also"></a>См. также  
 [Свойство ActiveConnection (ADOX)](./activeconnection-property-adox.md)   
 [Объект каталога (ADOX)](./catalog-object-adox.md)   
 [Объект Column (ADOX)](./column-object-adox.md)   
 [Коллекция Columns (ADOX)](./columns-collection-adox.md)   
 [Объект Table (ADOX)](./table-object-adox.md)   
 [Коллекция Tables (ADOX)](./tables-collection-adox.md)   
 [Свойство Type (Table) (ADOX)](./type-property-table-adox.md)