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
manager: jroth
ms.openlocfilehash: 4763939e3eccd0bf4783df87141619cbc0fb011c
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702325"
---
# <a name="calling-a-stored-procedure-with-a-command"></a>Вызов хранимой процедуры с использованием команды
Команду можно использовать для вызова хранимой процедуры. Пример кода в конце этого раздела ссылается на хранимую процедуру в базе данных Northwind, вызывается CustOrdersOrders, который определен следующим образом.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 См. в документации SQL Server, Дополнительные сведения о том, как определение и вызов хранимых процедур.  
  
 Эта хранимая процедура аналогична команда, используемая в [параметров объекта команд](../../../ado/guide/data/command-object-parameters.md). Она принимает параметр идентификатора клиента и возвращает сведения о заказов этого клиента. В следующем образце кода использует эту хранимую процедуру как источник для ADO **записей**.  
  
 С помощью хранимой процедуры позволяет получить доступ к другой особенностью ADO: **параметры** коллекции **обновить** метод. С помощью этого метода, ADO можно автоматически заполнить все сведения о параметрах, необходимые для команды во время выполнения. Нет снижение производительности в использовании этого метода, так как ADO должны запросов к источнику данных, сведения о параметрах.  
  
 Другие различия между в следующем образце кода и кода в [параметров объекта команд](../../../ado/guide/data/command-object-parameters.md), где параметры были введены вручную. Во-первых, этот код не устанавливает **подготовленных** свойства **True** так как он является хранимой процедуры SQL Server и компилируется по определению. Во-вторых, **CommandType** свойство **команда** объект изменен на **adCmdStoredProc** во втором примере для информирования ADO, что команда выполнена хранимая процедура.  
  
 Наконец во втором примере параметр должно производиться по индексу при задании значения, так как может не известно имя параметра во время разработки. Если вы знаете имя параметра, можно задать новый [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) свойство **команда** объекта значение true и ссылаться на имя свойства. Может возникнуть вопрос, почему упомянутые позицию первого параметра в хранимую процедуру (@CustomerID)-1 вместо 0 (`objCmd(1) = "ALFKI"`). Это обусловлено параметр 0 содержит возвращаемое значение из хранимой процедуры SQL Server.  
  
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
  
## <a name="see-also"></a>См. также  
 [Статье базы знаний 117500](https://go.microsoft.com/fwlink/?LinkId=117500)
