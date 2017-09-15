---
title: "Вызов хранимой процедуры в качестве метода объекта соединения | Документы Microsoft"
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
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 35ffdb79-a931-4271-a3bb-0cd804cf173e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d9ddfc9497f744e2904ae06fa32e93887ae5080
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="calling-a-stored-procedure-as-a-method-on-a-connection-object"></a>Вызов хранимой процедуры в качестве метода объекта подключения
Можно вызвать хранимую процедуру, как если бы оно метода машинного кода при открытии связанного **подключения** объекта. Это похоже на вызов именованную команду для **подключения** объекта.  
  
 В следующем примере кода Visual Basic вызывает хранимую процедуру в базе данных Northwind, вызывается CustOrdersOrders, который указан здесь еще раз для удобства.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 В следующем примере кода демонстрируется вызов хранимой процедуры, как если бы оно собственного метода на открытый связанный **подключения** объекта.  
  
```  
Const DS = "MySQLServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim objConn As New ADODB.Connection  
Dim objRs As New ADODB.Recordset  
Dim objComm As New ADODB.Command  
  
ConnectionString = "Provider=" & DP & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;"  
  
' Connect to the data source.  
objConn.Open ConnectionString  
  
' Set a stored procedure  
  
Set objComm.ActiveConnection = objConn  
  
' Execute the stored procedure on  
' the active connection object...  
'    "ALFKI" is the required input parameter,  
'    objRs is the resultant output variable.  
  
' Display the result.  
Debug.Print "Results returned from sp_CustOrdersOrders for ALFKI: "  
Do While Not objRs.EOF  
    Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                objRs(2) & vbTab & objRs(3)  
    objRs.MoveNext  
 Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
Set objComm = Nothing  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
