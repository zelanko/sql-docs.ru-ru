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
author: rothja
ms.author: jroth
ms.openlocfilehash: d172e86659496332ec02bb87af6e237061edc571
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761380"
---
# <a name="ado-run-time-errors"></a>Ошибки времени выполнения ADO
Ошибки ADO сообщаются в программе как ошибки времени выполнения. Для их перехвата и обработкой можно использовать механизм перехвата ошибок на языке программирования. Например, в Visual Basic используйте оператор **On Error** . В Visual C++ это зависит от метода, используемого для доступа к библиотекам ADO. С #import используйте блок **try-catch** . В противном случае программистам C++ необходимо явно получить объект Error, вызвав **жетерроринфо**. Следующая Visual Basic подпроцедура демонстрирует перехват ошибки ADO:

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

 Эта процедура **Form_Load** события намеренно создает ошибку, пытаясь дважды открыть один и тот же объект **соединения** . Во второй раз, когда вызывается метод **Open** , активируется обработчик ошибок. В этом случае ошибка относится к типу **адерробжектопен**, поэтому обработчик ошибок отображает следующее сообщение перед возобновлением выполнения программы:

```
Error #3705: Operation is not allowed when the object is open.
Error reported by: ADODB.Connection
Help File: E:\WINNT\HELP\ADO260.CHM Topic ID: 1003705
```

 Сообщение об ошибке содержит все сведения, предоставляемые объектом Visual Basic **Err** , за исключением значения **ластдллеррор** , которое здесь не применяется. Номер ошибки сообщает, какая ошибка возникла. Описание полезно в случаях, когда не нужно самостоятельно выполнять обработку ошибки. Вы можете просто передать его пользователю. Несмотря на то, что обычно требуется использовать сообщения, настроенные для вашего приложения, вы не сможете ожидать каждой ошибки. Описание дает некоторые сведения о том, что пошло не так. В примере кода ошибка была передана объектом **Connection** . Вы увидите тип объекта или программный идентификатор здесь — не имя переменной.

> [!NOTE]
>  Объект Visual Basic **Err** содержит только сведения о последней ошибке. Коллекция **ошибок** ADO объекта **Connection** содержит один объект **Error** для каждой ошибки, вызванной самой последней операцией ADO. Для решения нескольких ошибок используйте коллекцию **Errors** , а не объект **Err** . Дополнительные сведения о сборе **ошибок** см. в разделе [ошибки поставщика](../../../ado/guide/data/provider-errors.md). Однако если нет допустимого объекта **соединения** , то объект **Err** является единственным источником сведений об ошибках ADO.

 Какие типы операций могут вызвать ошибки ADO? Распространенные ошибки ADO могут привести к открытию объекта, например **подключения** или **набора записей**, попытке обновить данные или вызов метода или свойства, которые не поддерживаются поставщиком.

 OLE DB ошибки также могут передаваться в приложение в виде ошибок во время выполнения в коллекции **Errors** .

 В следующем разделе приведены дополнительные сведения об ошибках ADO.

-   [Справочник по ошибкам ADO](../../../ado/guide/data/ado-error-reference.md)
