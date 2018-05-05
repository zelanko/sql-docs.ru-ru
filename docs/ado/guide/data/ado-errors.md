---
title: Ошибки ADO | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO]
ms.assetid: 9bb84114-a1df-4122-a1b8-ad98dcd85cc3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a36f5b96ac0c04b6315ba5a135bbab0dbe75df2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ado-run-time-errors"></a>Ошибки во время выполнения ADO
Ошибки во время выполнения ошибки ADO фиксируются в программу. Перехват ошибок механизма язык программирования позволяет перехватывать и обрабатывать их. Например, в Visual Basic, используйте **On Error** инструкции. В Visual C++ он зависит от метода, используемого для доступа к библиотекам ADO. С помощью #import, использовать **try-catch-** блока. В противном случае программистов C++ необходимо явным образом получать объект ошибки путем вызова **GetErrorInfo**. Приведенная ниже процедура sub в Visual Basic демонстрирует перехват ошибка ADO:

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

 Это **Form_Load** процедуру обработки события намеренно создает ошибку при попытке открыть же **подключения** объекта дважды. Во второй раз **откройте** вызывается метод, активируется обработчика ошибок. В этом случае ошибка является типа **adErrObjectOpen**, поэтому обработчик ошибок перед возобновлением выполнения программы будет отображаться следующее сообщение:

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 Сообщение об ошибке включает каждую часть сведений, предоставляемых в Visual Basic **Err** объекта, за исключением **LastDLLError** значение, которое здесь не применим. Номер ошибки указывает, какая ошибка. Описание полезно в случаях, в которых вы не хотите самостоятельно обрабатывать ошибки. Можно просто передать его вместе для пользователя. Несмотря на то, что обычно требуется использовать сообщения, настроенные для приложения, невозможно предугадать каждой ошибке; Описание предоставляет некоторые понять, что пошло не так. В образце кода произошла ошибка **подключения** объекта. Вы увидите здесь программный код или тип объекта, не имя переменной.

> [!NOTE]
>  В Visual Basic **Err** объект содержит только сведения о последней ошибке. ADO **ошибки** коллекцию **подключения** объект содержит одно **ошибка** объект для каждой ошибки, вызванные последней операции ADO. Используйте **ошибки** коллекции, а не **Err** объектов для обработки нескольких ошибок. Дополнительные сведения о **ошибки** коллекции, в разделе [ошибки поставщика](../../../ado/guide/data/provider-errors.md). Тем не менее если нет допустимых **подключения** объекта, **Err** объект является единственным источником для получения сведений об ошибках ADO.

 Определяет, какие типы операций, вероятно появление ошибок ADO? Распространенные ошибки ADO может включать в себя открывающей объекта, например **подключения** или **записей**, попытка обновления данных или вызовом метода или свойства, которое не поддерживается поставщиком.

 Также можно передать ошибок OLE DB в приложение как ошибки во время выполнения в **ошибки** коллекции.

 Следующий раздел содержит дополнительные сведения об ошибках ADO.

-   [Справочник по ошибкам ADO](../../../ado/guide/data/ado-error-reference.md)
