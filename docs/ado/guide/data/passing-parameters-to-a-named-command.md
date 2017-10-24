---
title: "Передача параметров именованную команду | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named commands [ADO]
- commands [ADO], passing parameters to a named command
ms.assetid: 36e0cdbe-7f50-40f5-af0d-700f5d8dc75a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 33d1ee3fe4e24695deccd0615f17868bfdfd988c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="passing-parameters-to-a-named-command"></a>Передача параметров в именованную команду
Точно так же как результат выполнения команды, передается вовне как *out* переменной именованного команды, параметры для параметризованной команды можно было передан в качестве *в* переменные для именованной команды.  
  
 В следующем примере кода в примере разместить пытается получить все заказы для клиента, **CustomerID** — «ALKFI» из базы данных "Борей". Значение **CustomerID** указывается во время, когда вызывается именованную команду.  
  
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
  
 Обратите внимание, что все входные параметры должны указываться до любой выходная переменная типы данных параметров должны совпадать, или могут быть преобразованы отличающиеся от соответствующих полей. Следующая инструкция:  
  
```  
objConn.GetOrdersOf 12345, objRs  
```  
  
 — вызовет ошибку несогласованных типов данных, поскольку требуется входной параметр имеет **строка** типа, отличного от **целое число со знаком** типа.  
  
 Следующий вызов:  
  
```  
objConn.GetOrdersOf "12345", objRs  
```  
  
 — является допустимой, однако вернет пустой результирующий набор, потому что записи не существует в базе данных.  
  
## <a name="see-also"></a>См. также:  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)

