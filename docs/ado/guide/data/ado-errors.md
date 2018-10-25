---
title: Ошибки ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO]
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4fadb19aac4700738f4c6ec43449b3de7d4a4a18
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776372"
---
# <a name="ado-run-time-errors"></a>Ошибки времени выполнения ADO
Ошибки ADO выводятся в программу как ошибки во время выполнения. Механизм перехвата ошибок в языке программирования позволяет перехватывать и обрабатывать их. Например, в Visual Basic, используется **On Error** инструкции. В Visual C++ механизм зависит от метода, используемого для доступа к библиотеки ADO. С помощью #import, используется **try-catch** блока. В противном случае нужно явно получить объект error, вызвав программисты на C++ **GetErrorInfo**. Приведенная ниже процедура sub в Visual Basic демонстрирует перехват ошибка ADO:

```
' BeginErrorHandlingVB01
Private Sub Form_Load()
' Turn on error handling
On Error GoTo FormLoadError

'Open the database and the recordset for processing.
'
Dim strCnn As String
strCnn = "Provider=sqloledb;" & _
    "Data Source=a-iresmi2000;" & _
    "Initial Catalog=Northwind;Integrated Security=SSPI"

' cnn is a Public Connection Object because
' it was defined WithEvents
Set cnn = New ADODB.Connection
cnn.Open strCnn

' The next line of code intentionally causes
' an error by trying to open a connection
' that has already been opened.
cnn.Open strCnn

' rst is a Public Recordset because it
' was defined WithEvents
Set rst = New ADODB.Recordset
rst.Open "Customers", cnn

Exit Sub

' Error handler
FormLoadError:
    Dim strErr As String
    Select Case Err
        Case adErrObjectOpen
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            strErr = strErr & "Error reported by: " & Err.Source & vbCrLf
            strErr = strErr & "Help File: " & Err.HelpFile & vbCrLf
            strErr = strErr & "Topic ID: " & Err.HelpContext
            MsgBox strErr
            Debug.Print strErr
            Err.Clear
            Resume Next
        ' If some other error occurs that
        ' has nothing to do with ADO, show
        ' the number and description and exit.
        Case Else
            strErr = "Error #" & Err.Number & ": " & Err.Description & vbCrLf
            MsgBox strErr
            Debug.Print strErr
            Unload Me
    End Select
End Sub
' EndErrorHandlingVB01
```

 Это **Form_Load** процедуру обработки события намеренно создает ошибку, попытайтесь открыть же **подключения** объект дважды. Во второй раз **откройте** вызывается метод, активируется, обработчик ошибок. В этом случае ошибка имеет тип **adErrObjectOpen**, поэтому обработчик ошибок отображается следующее сообщение перед возобновлением выполнения программы:

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 Сообщение об ошибке включает в себя каждого фрагмента данных, предоставляемых Visual Basic **Err** объекта, за исключением **LastDLLError** значение, которое здесь не применим. Номер ошибки рассказывается о том, какая именно ошибка произошла. Описание полезно в случаях, в которых нежелательно для обработки ошибки самостоятельно. Можно просто передать его пользователю. Несмотря на то, что обычно требуется использовать сообщения, настроенные для вашего приложения, не может предвидеть каждой ошибке; Описание предоставляет некоторые понять, что пошло не так. В образце кода, сообщила об ошибке **подключения** объекта. Вы увидите тип объекта или программный идентификатор здесь — не имя переменной.

> [!NOTE]
>  В Visual Basic **Err** объект содержит только сведения о последней произошедшей ошибке. ADO **ошибки** коллекцию **подключения** объект содержит одно **ошибка** объект для каждой ошибки, вызванные последней операции ADO. Используйте **ошибки** коллекции, а не **Err** объекта для обработки нескольких ошибок. Дополнительные сведения о **ошибки** коллекции, см. в разделе [ошибки поставщика](../../../ado/guide/data/provider-errors.md). Тем не менее если отсутствует **подключения** объекта, **Err** объекта является единственным источником сведения об ошибках ADO.

 Какие типы операций могут привести к ошибкам ADO? Распространенные ошибки ADO может включать в себя такие как открытие объекта **подключения** или **записей**, пытается обновить базу данных или вызов метода или свойства, которое не поддерживается поставщиком.

 Ошибки OLE DB также можно передать в приложение как ошибки времени выполнения в **ошибки** коллекции.

 Следующий раздел содержит дополнительные сведения об ошибках ADO.

-   [Справочник по ошибкам ADO](../../../ado/guide/data/ado-error-reference.md)
