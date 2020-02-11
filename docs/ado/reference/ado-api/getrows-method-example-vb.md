---
title: Пример метода GetRows (Visual Basic) | Документация Майкрософт
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
- Getrows method [ADO], Visual Basic example
ms.assetid: 9f7c78bb-7bb8-4c4f-8e5a-4d3bfc8a208f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fedde638e343281c5d3810cc80c9ba8db820e839
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918461"
---
# <a name="getrows-method-example-vb"></a>Пример метода GetRows (Visual Basic)
В этом примере метод [GetRows](../../../ado/reference/ado-api/getrows-method-ado.md) используется для получения указанного числа строк из [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) и для заполнения массива результирующими данными. Метод **GetRows** возвращает меньше требуемого числа строк в двух случаях: или, если был достигнут [конец файла](../../../ado/reference/ado-api/bof-eof-properties-ado.md) , или если **GetRows** попытался получить запись, удаленную другим пользователем. Функция возвращает **значение false** только в том случае, если происходит второй вариант. Для выполнения этой процедуры требуется функция Жетровсок.  
  
```  
'BeginGetRowsVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' connection and recordset variables  
    Dim rstEmployees As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strSQLEmployees As String  
    Dim strCnxn As String  
    ' array variable  
    Dim arrEmployees As Variant  
    ' detail variables  
    Dim strMessage As String  
    Dim intRows As Integer  
    Dim intRecord As Integer  
  
    ' open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' open recordset client-side to enable RecordCount  
    Set rstEmployees = New ADODB.Recordset  
    strSQLEmployees = "SELECT fName, lName, hire_date FROM Employee ORDER BY lName"  
    rstEmployees.Open strSQLEmployees, Cnxn, adOpenStatic, adLockReadOnly, adCmdText  
  
    ' get user input for number of rows  
    Do  
        strMessage = "Enter number of rows to retrieve:"  
        intRows = Val(InputBox(strMessage))  
  
          ' if bad user input exit the loop  
        If intRows <= 0 Then  
            MsgBox "Please enter a positive number", vbOKOnly, "Not less than zero!"  
        ' if number of requested records is over the total  
        ElseIf intRows > rstEmployees.RecordCount Then  
            MsgBox "Not enough records in Recordset to retrieve " & intRows & " rows.", _  
            vbOKOnly, "Over the available total"  
        Else  
            Exit Do  
        End If  
    Loop  
  
      ' else put the data in an array and print  
    arrEmployees = rstEmployees.GetRows(intRows)  
  
    Dim x As Integer, y As Integer  
  
    For x = 0 To intRows - 1  
        For y = 0 To 2  
            Debug.Print arrEmployees(y, x) & " ";  
        Next y  
        Debug.Print vbCrLf  
    Next x  
  
    ' clean up  
    rstEmployees.Close  
    Cnxn.Close  
    Set rstEmployees = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndGetRowsVB  
```  
  
## <a name="see-also"></a>См. также:  
 [Метод GetRows (ADO)](../../../ado/reference/ado-api/getrows-method-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
