---
title: "Изменение данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, editing data
- AdUseClient [ADO]
- editing data [ADO]
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 89d3f549d52b522cdd6668599e114997bd908511
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="editing-data"></a>Редактирование данных
Было показано, как использовать ADO для подключения к источнику данных, выполнить команду, получить результаты в **набора записей** объекта и перемещение в **набора записей**. В этом разделе рассматриваются основные след ADO: изменения данных.  
  
 В этом разделе по-прежнему использовать образец **записей** появился в [проверки данных](../../../ado/guide/data/examining-data.md), с одним важным изменением. Следующий код используется для открытия **записей**:  
  
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
  
 Важные изменения в код включает в себя параметр **CursorLocation** свойство **подключения** равное **adUseClient** в  *GetNewConnection* (показано в следующем примере), функции, которая указывает на использование клиентских курсоров. Дополнительные сведения о различиях между клиентских и серверных курсоров см. в разделе [основные сведения о курсорах и блокировок](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 **CursorLocation** свойства **adUseClient** параметр перемещает положение курсора из источника данных (SQL Server, в данном случае) расположение кода клиента (настольной рабочей станции). Этот параметр принудительно ADO вызываемый обработчик курсора клиента для OLE DB для клиента, чтобы создавать и управлять ими курсор.  
  
 Вы также заметили, **LockType** параметр **откройте** метод изменен на **adLockBatchOptimistic**. Это открывает курсор в пакетном режиме. (Поставщик кэширует внесение нескольких изменений и записывает их в базовом источнике данных только при вызове **UpdateBatch** метод.) Изменения, внесенные в **записей** не будут обновлены в базе данных до **UpdateBatch** вызывается метод.  
  
 Наконец код в этом разделе используется измененная версия GetNewConnection функции. Эта версия функции теперь возвращает клиентского курсора. Функция выглядит следующим образом:  
  
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
  
-   [Варианты: с помощью инструкций SQL](../../../ado/guide/data/alternatives-using-sql-statements.md)
