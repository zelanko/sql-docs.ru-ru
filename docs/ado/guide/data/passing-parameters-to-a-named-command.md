---
description: Передача параметров именованной команде
title: Передача параметров в именованную команду | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- named commands [ADO]
- commands [ADO], passing parameters to a named command
ms.assetid: 36e0cdbe-7f50-40f5-af0d-700f5d8dc75a
author: rothja
ms.author: jroth
ms.openlocfilehash: 6de01bb420a7e2c5fadd2970064d5e84d22328b3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980145"
---
# <a name="passing-parameters-to-a-named-command"></a>Передача параметров именованной команде
Точно так же, как результат выполнения команды передается как переменная *out* из именованной команды, параметры для параметризованной команды могут передаваться в качестве переменных *в* именованную команду.  
  
 В следующем примере кода предпринимается попытка извлечь все заказы, размещенные Клиентом, чей **идентификатор клиента** — «алкфи» из базы данных «Борей». Значение **CustomerID** указывается во время вызова именованной команды.  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim objConn As New ADODB.Connection  
Dim objRs As New ADODB.Recordset  
Dim objComm As New ADODB.Command  
  
CommandText = "SELECT OrderID, OrderDate, " & _  
                     "RequiredDate, ShippedDate " & _  
                     "FROM Orders " & _  
                     "WHERE CustomerID = ? " & _  
                     "ORDER BY OrderID"  
  
ConnectionString = "Provider=" & DP & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;"  
  
' Connect to the data source.  
objConn.Open ConnectionString  
  
' Set a named command.  
objComm.CommandText = CommandText  
objComm.CommandType = adCmdText  
objComm.Name = "GetOrdersOf"  
Set objComm.ActiveConnection = objConn  
  
' Call the named command, passing a CustomerID value  
' as the input parameter.   
'    "ALFKI" is the required input parameter,  
'    objRs is the resultant output variable.  
objConn.GetOrdersOf "ALKFI", objRs  
  
' Display the result.  
Debug.Print "All orders by ALFKI:"  
Do While Not objRs.EOF  
    Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                objRs(2) & vbTab & objRs(3)  
    objRs.MoveNext  
Loop  
  
' Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
Set objComm = Nothing  
```  
  
 Обратите внимание, что все входные параметры должны предшествовать любой выходной переменной, а типы данных параметров должны совпадать, или их можно преобразовать в соответствующие поля. Следующая инструкция:  
  
```  
objConn.GetOrdersOf 12345, objRs  
```  
  
 — приведет к ошибке несовпадающих типов данных, так как обязательный входной параметр имеет **строковый** тип, а не **целочисленный** тип.  
  
 Следующий вызов  
  
```  
objConn.GetOrdersOf "12345", objRs  
```  
  
 — является допустимым, но выдаст пустой результирующий набор, так как в базе данных не существует таких записей.  
  
## <a name="see-also"></a>См. также  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
