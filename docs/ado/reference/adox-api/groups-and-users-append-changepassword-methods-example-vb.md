---
title: Группы и пользователи Append, пример метода ChangePassword (Visual Basic) | Документация Майкрософт
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
- ChangePassword method [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 50e0aeae082ad3ad70462c172a3dfaa157047411
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712042"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>Примеры методов Append коллекций Groups и Users, а также пример метода ChangePassword (Visual Basic)
В этом примере показано [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) метод [группы](../../../ado/reference/adox-api/groups-collection-adox.md), а также [Append](../../../ado/reference/adox-api/append-method-adox-users.md) метод [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) путем добавления новых [Группы](../../../ado/reference/adox-api/group-object-adox.md) и новый [пользователя](../../../ado/reference/adox-api/user-object-adox.md) в системе. Новый **группы** добавляется к **группы** коллекции нового **пользователя**. Следовательно, новый **пользователя** добавляется **группы**. Кроме того [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) метод используется для указания **пользователя** пароль.  
  
> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.  
  
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
 [Append-метод (коллекция Groups ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-метод (коллекция Users ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Метод ChangePassword (ADOX)](../../../ado/reference/adox-api/changepassword-method-adox.md)   
 [Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)   
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
