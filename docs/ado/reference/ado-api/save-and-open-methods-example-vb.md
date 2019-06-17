---
title: Сохранение и открытие примеры методов (Visual Basic) | Документация Майкрософт
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
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 32ed7e6240f5f9622bfcb80e2f05a633fcaf2fdc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711633"
---
# <a name="save-and-open-methods-example-vb"></a>Примеры методов Save и Open (Visual Basic)
Этих трех примерах показано, как [Сохранить](../../../ado/reference/ado-api/save-method.md) и [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) методы, которые могут использоваться совместно.  
  
 Предполагается, что будет в командировки и хотите взять с собой таблицы из базы данных. Перед тем как перейти, доступе к данным как [записей](../../../ado/reference/ado-api/recordset-object-ado.md) и сохраните его в виде переносимые. При поступлении в пункт назначения, можно получить доступ к **записей** как локальный, отключен **записей**. При внесении изменений в **записей**, а затем сохраните его. Наконец когда вы возвращаетесь домой, попытку соединения с базой данных и применить его изменения, внесенные в дороге.  
  
 Во-первых, доступ к и сохранить ***авторы*** таблицы.  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 На этом этапе вы попасть в пункт назначения. Вы будете обращаться к ***авторов*** таблицы как локальный, отключен **записей**. Необходимо иметь **MSPersist** поставщика на компьютере, используемом для доступа к сохраненному файлу a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Наконец можно вернуться на домашнюю страницу. Теперь можно обновите базу данных с изменениями.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Дополнительные сведения о сохраняемости набора записей](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
