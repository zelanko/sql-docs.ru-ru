---
title: Редактирование данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, editing data
- AdUseClient [ADO]
- editing data [ADO]
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8e8fd90849b8e046a7f4fe5d158d4594e612c91f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925495"
---
# <a name="editing-data"></a>Изменение данных
Мы объяснили как использовать ADO для подключения к источнику данных, выполнение команды, получить результаты в **записей** , а также перемещаться **записей**. Этот раздел посвящен следующей фундаментальные операции ADO: редактирование данных.  
  
 В этом разделе будет продолжать использовать образец **набор записей** появился в [проверки данных](../../../ado/guide/data/examining-data.md), с одним важным изменением. Следующий код используется для открытия **записей**:  
  
```  
'BeginEditIntro  
    Dim strSQL As String  
    Dim objRs1 As ADODB.Recordset  
  
    strSQL = "SELECT * FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
  
    objRs1.Open strSQL, GetNewConnection, adOpenStatic, _  
                adLockBatchOptimistic, adCmdText  
  
    ' Disconnect the Recordset from the Connection object.  
    Set objRs1.ActiveConnection = Nothing  
'EndEditIntro  
```  
  
 Важные изменения в код предполагает установку **CursorLocation** свойство **подключения** равное **adUseClient** в  *GetNewConnection* (показано в следующем примере), функции, который указывает на использование клиентского курсора. Дополнительные сведения о различиях между клиентские и серверные курсоры, см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 **CursorLocation** свойства **adUseClient** параметр расположение курсора из источника данных (SQL Server, в данном случае) перемещается в заданную позицию клиентского кода (настольной рабочей станции). Этот параметр заставляет ADO для вызова на клиенте, чтобы создавать и управлять ими курсор обработчик курсора клиента для OLE DB.  
  
 Можно также заметить, **LockType** параметр **откройте** метод изменено на **adLockBatchOptimistic**. Это открывает курсор в пакетном режиме. (Поставщик кэширует несколько изменений и записывает их в базовом источнике данных только в том случае, когда вы вызываете **UpdateBatch** метод.) Изменения, внесенные в **записей** не будут обновлены в базе данных до **UpdateBatch** вызывается метод.  
  
 Наконец код в этом разделе используется измененная версия GetNewConnection функции. Эта версия функции теперь возвращает клиентский курсор. Функция выглядит следующим образом:  
  
```  
'BeginNewConnection  
Public Function GetNewConnection() As ADODB.Connection  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim strConnStr As String  
  
    strConnStr = "Provider='SQLOLEDB';Initial Catalog='Northwind';" & _  
                 "Data Source='MySqlServer';Integrated Security='SSPI';"  
  
    objConn.ConnectionString = strConnStr  
    objConn.CursorLocation = adUseClient  
    objConn.Open  
  
    Set GetNewConnection = objConn  
  
    Exit Function  
  
ErrHandler:  
    Set objConn = Nothing  
    Set GetNewConnection = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Function  
'EndNewConnection  
```  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Изменение существующих записей](../../../ado/guide/data/editing-existing-records.md)  
  
-   [Добавление записей](../../../ado/guide/data/adding-records.md)  
  
-   [Определение поддерживаемых возможностей](../../../ado/guide/data/determining-what-is-supported.md)  
  
-   [Удаление записей с помощью метода Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md)  
  
-   [Альтернативные варианты: С помощью инструкций SQL](../../../ado/guide/data/alternatives-using-sql-statements.md)
