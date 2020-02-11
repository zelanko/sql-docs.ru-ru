---
title: Вызов хранимой процедуры с помощью команды | Документация Майкрософт
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
ms.assetid: 685f7652-2271-4ede-b552-2eeb8c756b4c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 32f1013ef0aa9c8f02e19ec98234418480bc5f22
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925867"
---
# <a name="calling-a-stored-procedure-with-a-command"></a>Вызов хранимой процедуры с использованием команды
Для вызова хранимой процедуры можно использовать команду. Пример кода в конце этого раздела относится к хранимой процедуре в образце базы данных Northwind, именуемой Кустордерсордерс, которая определяется следующим образом.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 Дополнительные сведения об определении и вызове хранимых процедур см. в документации по SQL Server.  
  
 Эта хранимая процедура аналогична команде, используемой в [параметрах объекта команды](../../../ado/guide/data/command-object-parameters.md). Он принимает параметр идентификатора клиента и возвращает сведения о заказах этого клиента. В следующем примере кода эта хранимая процедура используется в качестве источника для **набора записей**ADO.  
  
 Использование хранимой процедуры позволяет получить доступ к другой возможности ADO: метод **обновления** коллекции **параметров** . С помощью этого метода ADO может автоматически заполнять всю информацию о параметрах, необходимых команде во время выполнения. Использование этой методики приводит к снижению производительности, поскольку ADO должен запрашивать у источника данных сведения о параметрах.  
  
 Существуют другие важные различия между следующим образцом кода и кодом в [параметрах объекта Command](../../../ado/guide/data/command-object-parameters.md), где параметры были указаны вручную. Во-первых, этот код не устанавливает свойство **Prepared** в **значение true** , поскольку оно является SQL Server хранимой процедурой и предкомпилировано по определению. Во-вторых, свойство **CommandType** объекта **Command** изменилось на **адкмдсторедпрок** во втором примере, чтобы информировать ADO о том, что команда была хранимой процедурой.  
  
 Наконец, во втором примере при задании значения параметр должен называться индексом, поскольку имя параметра во время разработки может быть неизвестно. Если известно имя параметра, можно задать для нового свойства [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) объекта **Command** значение true и указать имя свойства. Может возникнуть вопрос, почему первым параметром, упомянутым в хранимой процедуре (@CustomerID), является 1, а не`objCmd(1) = "ALFKI"`0 (). Это происходит потому, что параметр 0 содержит возвращаемое значение из SQL Server хранимой процедуры.  
  
```  
'BeginAutoParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set CommandText equal to the stored procedure name.  
    objCmd.CommandText = "CustOrdersOrders"  
    objCmd.CommandType = adCmdStoredProc  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Automatically fill in parameter info from stored procedure.  
    objCmd.Parameters.Refresh  
  
    ' Set the param value.  
    objCmd(1) = "ALFKI"  
  
    ' Execute once and display...  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' ...then set new param value, re-execute command, and display.  
    objCmd(1) = "CACTU"  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndAutoParamCmd  
  
'BeginNewConnection  
Private Function GetNewConnection() As ADODB.Connection  
    Dim oCn As New ADODB.Connection  
    Dim sCnStr As String  
  
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    oCn.Open sCnStr  
  
    If oCn.State = adStateOpen Then  
        Set GetNewConnection = oCn  
    End If  
  
End Function  
'EndNewConnection  
```  
  
## <a name="see-also"></a>См. также:  
 [Статья базы знаний 117500](https://go.microsoft.com/fwlink/?LinkId=117500)
