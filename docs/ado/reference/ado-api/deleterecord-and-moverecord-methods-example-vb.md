---
description: Примеры методов Делетерекорд и MoveRecord (Visual Basic)
title: Примеры методов Делетерекорд и MoveRecord (Visual Basic) | Документация Майкрософт
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
- MoveRecord method [ADO], Visual Basic example
- DeleteRecord method [ADO], Visual Basic example
ms.assetid: c3937d1e-9872-47e5-a22e-b147637f2388
author: rothja
ms.author: jroth
ms.openlocfilehash: a3cb757703b7eebd3734ee33b97205e6491a4c40
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444126"
---
# <a name="deleterecord-and-moverecord-methods-example-vb"></a>Примеры методов Делетерекорд и MoveRecord (Visual Basic)
В этом примере показано, как копировать, перемещать, изменять и удалять содержимое текстового файла, опубликованного в веб-папке. Другие используемые свойства и методы включают [дочерние элементы](../../../ado/reference/ado-api/getchildren-method-ado.md), [парентурл](../../../ado/reference/ado-api/parenturl-property-ado.md), [источник](../../../ado/reference/ado-api/source-property-ado-record.md)и [запись на диск](../../../ado/reference/ado-api/flush-method-ado.md).  
  
```  
'BeginDeleteRecordVB  
  
'Note:  
' IIS must be running for this sample to work. To  
' use this sample you must:  
'  
' 1. create folders named "test" and "test2"  
'    in the root web folder of https://MyServer  
'  
' 2. Create a text file named "test2.txt" in the  
'    "test" folder.  
' 3. Replace "MyServer" with the appropriate web  
'    server name.  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' connection and recordset variables  
    Dim rsDestFolder As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
  
     ' file as record variables  
    Dim rcFile As ADODB.Record  
    Dim rcDestFile As ADODB.Record  
    Dim rcDestFolder As ADODB.Record  
    Dim objStream As Stream  
  
     ' file variables  
    Dim strFile As String  
    Dim strDestFile As String  
    Dim strDestFolder As String  
  
     ' instantiate variables  
    Set rsDestFolder = New ADODB.Recordset  
    Set rcDestFolder = New ADODB.Record  
    Set rcFile = New ADODB.Record  
    Set rcDestFile = New ADODB.Record  
    Set objStream = New ADODB.Stream  
  
     ' open a record on a text file  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "url=https://MyServer/"  
    Cnxn.Open strCnxn  
    strFile = "test/test2.txt"  
    rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection  
    Debug.Print Cnxn  
  
     ' edit the contents of the text file  
    objStream.Open rcFile, , adOpenStreamFromRecord  
  
    Debug.Print "Source: " & strCnxn & rcFile.Source  
    Debug.Print "Original text: " & objStream.ReadText  
  
    objStream.Position = 0  
    objStream.WriteText "Newer Text. "  
    objStream.Position = 0  
  
    Debug.Print "New text: " & objStream.ReadText  
  
     ' reset the stream object  
    objStream.Flush  
    objStream.Close  
    rcFile.Close  
  
     ' reopen record to see new contents of text file  
    rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection  
    objStream.Open rcFile, adModeReadWrite, adOpenStreamFromRecord  
  
    Debug.Print "Source: " & strCnxn & rcFile.Source  
    Debug.Print "Edited text: " & objStream.ReadText  
  
     ' copy the file to another folder  
    strDestFile = "test2/test1.txt"  
    rcFile.CopyRecord "", "https://MyServer/" & strDestFile, "", "", adCopyOverWrite  
  
     ' delete the original file  
    rcFile.DeleteRecord  
  
     ' move the file from the subfolder back to original location  
    strDestFolder = "test2/"  
    rcDestFolder.Open strDestFolder, Cnxn ', adOpenIfExists  'Or adCreateCollection  
    Set rsDestFolder = rcDestFolder.GetChildren  
    rsDestFolder.MoveFirst  
  
     ' position current record at on the correct file  
    Do While Not (rsDestFolder.EOF Or rsDestFolder(0) = "test1.txt")  
        rsDestFolder.MoveNext  
    Loop  
  
     ' open a record on the correct row of the recordset  
    rcDestFile.Open rsDestFolder, Cnxn  
  
     ' do the move  
    rcDestFile.MoveRecord "", "https://MyServer/" & strFile, "", "", adMoveOverWrite  
  
    ' clean up  
    rsDestFolder.Close  
    Cnxn.Close  
    Set rsDestFolder = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rsDestFolder Is Nothing Then  
        If rsDestFolder.State = adStateOpen Then rsDestFolder.Close  
    End If  
    Set rsDestFolder = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndDeleteRecordVB  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод Делетерекорд (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)   
 [Метод Flush (ADO)](../../../ado/reference/ado-api/flush-method-ado.md)   
 [Метод дочернего элемента (ADO)](../../../ado/reference/ado-api/getchildren-method-ado.md)   
 [Метод MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)   
 [Свойство Парентурл (ADO)](../../../ado/reference/ado-api/parenturl-property-ado.md)   
 [Свойство Source (объект Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)
