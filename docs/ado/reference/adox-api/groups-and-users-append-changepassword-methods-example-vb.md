---
description: Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)
title: Добавление в группы и пользователей, пример методов ChangePassword (Visual Basic) | Документация Майкрософт
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
- ChangePassword method [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
author: rothja
ms.author: jroth
ms.openlocfilehash: 824cf44560335152ac6079c4ff61f2177368447c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984385"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)
В этом примере демонстрируется метод [append](./append-method-adox-groups.md) [групп](./groups-collection-adox.md), а также метод [добавления](./append-method-adox-users.md) [пользователей](./users-collection-adox.md) путем добавления новой [группы](./group-object-adox.md) и нового [пользователя](./user-object-adox.md) в систему. Новая **Группа** добавляется в коллекцию **Groups** нового **пользователя**. Таким образом, новый **пользователь** добавляется в **группу**. Кроме того, метод [ChangePassword](./changepassword-method-adox.md) используется для указания пароля **пользователя** .  
  
> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.  
  
```  
' BeginGroupVB  
Sub Main()  
    On Error GoTo GroupXError  
  
    Dim cat As ADOX.Catalog  
    Dim usrNew As ADOX.User  
    Dim usrLoop As ADOX.User  
    Dim grpLoop As ADOX.Group  
  
    Set cat = New ADOX.Catalog  
  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';" & _  
        "jet oledb:system database=" & _  
        "'system.mdw'"  
  
    With cat  
        'Create and append new group with a string.  
        .Groups.Append "Accounting"  
  
        ' Create and append new user with an object.  
        Set usrNew = New ADOX.User  
        usrNew.Name = "Pat Smith"  
        usrNew.ChangePassword "", "Password1"  
        .Users.Append usrNew  
  
        ' Make the user Pat Smith a member of the  
        ' Accounting group by creating and adding the  
        ' appropriate Group object to the user's Groups  
        ' collection. The same is accomplished if a User  
        ' object representing Pat Smith is created and  
        ' appended to the Accounting group Users collection  
        usrNew.Groups.Append "Accounting"  
  
        ' Enumerate all User objects in the  
        ' catalog's Users collection.  
        For Each usrLoop In .Users  
            Debug.Print "  " & usrLoop.Name  
            Debug.Print "    Belongs to these groups:"  
            ' Enumerate all Group objects in each User  
            ' object's Groups collection.  
            If usrLoop.Groups.Count <> 0 Then  
                For Each grpLoop In usrLoop.Groups  
                    Debug.Print "    " & grpLoop.Name  
                Next grpLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next usrLoop  
  
        ' Enumerate all Group objects in the default  
        ' workspace's Groups collection.  
        For Each grpLoop In .Groups  
            Debug.Print "  " & grpLoop.Name  
            Debug.Print "    Has as its members:"  
            ' Enumerate all User objects in each Group  
            ' object's Users collection.  
            If grpLoop.Users.Count <> 0 Then  
                For Each usrLoop In grpLoop.Users  
                    Debug.Print "    " & usrLoop.Name  
                Next usrLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next grpLoop  
  
        ' Delete new User and Group objects because this  
        ' is only a demonstration.  
        ' These two line are commented out because the sub "OwnersX" uses  
        ' the group "Accounting".  
'        .Users.Delete "Pat Smith"  
'        .Groups.Delete "Accounting"  
  
    End With  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set usrNew = Nothing  
    Exit Sub  
  
GroupXError:  
  
    Set cat = Nothing  
    Set usrNew = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndGroupVB  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Append (группы ADOX)](./append-method-adox-groups.md)   
 [Метод Append (пользователи ADOX)](./append-method-adox-users.md)   
 [Объект каталога (ADOX)](./catalog-object-adox.md)   
 [Метод ChangePassword (ADOX)](./changepassword-method-adox.md)   
 [Объект Group (ADOX)](./group-object-adox.md)   
 [Коллекция Groups (ADOX)](./groups-collection-adox.md)   
 [Объект User (ADOX)](./user-object-adox.md)   
 [Коллекция Users (ADOX)](./users-collection-adox.md)