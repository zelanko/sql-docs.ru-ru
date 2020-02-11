---
title: Пример методов Save и Open (Visual Basic) | Документация Майкрософт
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
ms.openlocfilehash: 6d42488f8f167cc7c98f663478c742963d24253c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931197"
---
# <a name="save-and-open-methods-example-vb"></a>Примеры методов Save и Open (Visual Basic)
В этих трех примерах показано, как можно совместно использовать методы [Save](../../../ado/reference/ado-api/save-method.md) и [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) .  
  
 Предположим, что вы собираетесь в командировку и хотите взять таблицу из базы данных. Прежде чем перейти, вы получите доступ к данным в качестве [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) и сохраните их в переносимой форме. Когда вы приступите к назначению, вы получите доступ к **набору записей** как к локальному, отключенному **набору записей**. Вы вносите изменения в **набор записей**, а затем сохраняете его снова. Наконец, когда вы вернетесь домой, вы снова подключитесь к базе данных и обновите ее, внеся изменения, внесенные в дороге.  
  
 Сначала получите доступ к таблице ***authors*** и сохраните ее.  
  
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
  
 На этом этапе вы приступили к месту назначения. Вы будете обращаться к таблице ***authors*** как к локальному, отключенному **набору записей**. Необходимо иметь поставщик **мсперсист** на компьютере, который используется для доступа к сохраненному файлу, а:\пубс.ксмл.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Наконец, вы вернетесь домой. Теперь обновите базу данных с учетом внесенных изменений.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Дополнительные сведения о сохраняемости в наборе записей](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
