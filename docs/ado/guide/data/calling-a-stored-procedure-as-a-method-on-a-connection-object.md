---
description: Вызов хранимой процедуры в качестве метода объекта Connection
title: Вызов хранимой процедуры в качестве метода для объекта соединения | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 35ffdb79-a931-4271-a3bb-0cd804cf173e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e5e019760c4496b7dab769cb96fbd7b2eab4f47
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453706"
---
# <a name="calling-a-stored-procedure-as-a-method-on-a-connection-object"></a>Вызов хранимой процедуры в качестве метода объекта Connection
Хранимую процедуру можно вызвать, как если бы она была собственным методом для связанного открытого объекта **соединения** . Это похоже на вызов именованной команды для объекта **Connection** .  
  
 В следующем примере кода Visual Basic вызывается хранимая процедура в образце базы данных Northwind с именем Кустордерсордерс, которая снова указана для удобства.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 В следующем примере кода показано, как вызвать хранимую процедуру, как если бы она была собственным методом для связанного открытого объекта **соединения** .  
  
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
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
