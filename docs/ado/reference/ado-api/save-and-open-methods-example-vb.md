---
title: "Сохранение и открытие примере методы (Visual Basic) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7bf87da3c7a8e00b93c7e4055e6c957453fe658c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="save-and-open-methods-example-vb"></a>Сохранение и открытие примере методы (Visual Basic)
В следующих трех примерах как [Сохранить](../../../ado/reference/ado-api/save-method.md) и [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) методы, которые могут использоваться совместно.  
  
 Предположим, что происходит на командировки и нужно взять таблицы из базы данных. Перед тем как перейти, осуществляется доступ к данным как [записей](../../../ado/reference/ado-api/recordset-object-ado.md) и сохраните его в форме пересылать. При поступлении в пункт назначения, можно получить доступ к **записей** как локальные, отключен **записей**. Внести изменения в **записей**, а затем сохраните его. Наконец при возврате Главная соединиться с базой данных и дополнить изменения, внесенные в дороге.  
  
 Во-первых, доступ и сохраните ***авторы*** таблицы.  
  
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
  
 На этом этапе вы попали на месте назначения. Вы получите доступ к ***авторов*** таблицы как локальные, отключен **записей**. Необходимо иметь **MSPersist** поставщика на компьютере, который используется для доступа к сохраненному файлу a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Наконец можно вернуться на домашнюю страницу. Теперь можно обновите базу данных с изменениями.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>См. также  
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Дополнительные сведения о сохраняемости набора записей](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
