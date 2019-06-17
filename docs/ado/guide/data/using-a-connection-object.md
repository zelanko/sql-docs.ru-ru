---
title: Использование объекта Connection | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b19713028bcc5569a6a4aace4528e7c725cf7d0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704544"
---
# <a name="using-a-connection-object"></a>Использование объекта Connection
Прежде чем открывать **подключения** объекта, необходимо определить определенные сведения об источнике данных и тип подключения. Большая часть этой информации удерживается *ConnectionString* параметр [метод Open](../../../ado/reference/ado-api/open-method-ado-connection.md) на **подключения** объекта, или с помощью [ConnectionString Свойство](../../../ado/reference/ado-api/connectionstring-property-ado.md) на **подключения** объекта. Строка подключения состоит из списка пар аргументов и значений, разделенных точкой с запятой, значения, заключенные в одинарные кавычки. Пример:  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  Можно также указать имя источника ODBC данных (DSN) или файл Data Link (UDL) в строке подключения. Дополнительные сведения о источников данных, см. в разделе [Управление источниками данных](../../../odbc/admin/managing-data-sources.md) справочника по программированию ODBC. Дополнительные сведения о UDL, см. в разделе [Обзор API связи данных](https://msdn.microsoft.com/95c180ea-bd4f-4dca-b95a-576afd135bbc) справочника программиста OLE DB.  
  
 Как правило, установить соединение, вызвав **Connection.Open** метод с соответствующим *строку подключения* параметром. Пример показан в следующем фрагменте кода Visual Basic:  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 Здесь **oRs.Open** принимает **подключения** объекта (*oConn*) переменной в качестве значения его *ActiveConnection* параметра. Кроме того **Connection.CursorLocation** свойство принимает значение по умолчанию **adUseServer**. Сравните с [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) примере в предыдущем разделе. Следующая инструкция приведет к ошибкам.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
