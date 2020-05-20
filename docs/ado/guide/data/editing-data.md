---
title: Изменение данных | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: cc80c8ad9985efc21e2f583d8ca72751e21c1a2b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761040"
---
# <a name="editing-data"></a>Изменение данных
Мы объяснили, как использовать ADO для подключения к источнику данных, выполнять команду, получать результаты в объекте **набора записей** и перемещаться по **набору записей**. В этом разделе рассматриваются следующие фундаментальные операции ADO: Редактирование данных.  
  
 В этом разделе используется образец **набора записей** , представленный в статье [исследование данных](../../../ado/guide/data/examining-data.md)с одним важным изменением. Для открытия **набора записей**используется следующий код:  
  
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
  
 Важное изменение кода включает установку свойства **CursorLocation** объекта **Connection** , равного **адусеклиент** , в функции *жетневконнектион* (как показано в следующем примере), которая указывает на использование клиентского курсора. Дополнительные сведения о различиях между курсорами на стороне клиента и на стороне сервера см. в разделе [Основные сведения о курсорах и блокировках](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 Параметр **адусеклиент** свойства **CursorLocation** перемещает положение курсора из источника данных (SQL Server, в данном случае) в расположение клиентского кода (настольной рабочей станции). Этот параметр заставляет ADO вызывать модуль клиентского курсора для OLE DB на клиенте для создания курсора и управления им.  
  
 Также можно заметить, что параметр **LockType** метода **Open** изменен на **адлоккбатчоптимистик**. Курсор откроется в пакетном режиме. (Поставщик кэширует несколько изменений и записывает их в базовый источник данных только при вызове метода **UpdateBatch** ). Изменения, внесенные в **набор записей** , не будут обновлены в базе данных до тех пор, пока не будет вызван метод **UpdateBatch** .  
  
 Наконец, в коде в этом разделе используется измененная версия функции Жетневконнектион. Теперь эта версия функции возвращает курсор на стороне клиента. Функция выглядит следующим образом:  
  
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
