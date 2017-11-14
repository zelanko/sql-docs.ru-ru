---
title: "Вызов хранимой процедуры с помощью команды | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calling stored procedures [ADO]
- stored procedures [ADO]
- commands [ADO]
ms.assetid: 685f7652-2271-4ede-b552-2eeb8c756b4c
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 22af55f599bc6adafe6d1c6ea0dcb409033feeb0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="calling-a-stored-procedure-with-a-command"></a>Вызов хранимой процедуры с помощью команды
Команду можно использовать для вызова хранимой процедуры. Пример кода в конце этого раздела ссылается на хранимую процедуру в базе данных Northwind, вызывается CustOrdersOrders, которая определяется следующим образом.  
  
```  
CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS  
SELECT OrderID, OrderDate, RequiredDate, ShippedDate  
FROM Orders  
WHERE CustomerID = @CustomerID  
ORDER BY OrderID  
```  
  
 В разделе документации по SQL Server Дополнительные сведения об определении и вызов хранимых процедур.  
  
 Эта хранимая процедура подобна команда, используемая в [параметров объекта команд](../../../ado/guide/data/command-object-parameters.md). Он принимает параметр идентификатора клиента и возвращает сведения о заказов этого клиента. В следующем образце кода использует эту хранимую процедуру как источник для ADO **записей**.  
  
 С помощью хранимой процедуры позволяет получить доступ к еще одну функцию ADO: **параметры** коллекции **обновление** метод. С помощью этого метода, ADO может автоматически заполнять все сведения о параметрах, необходимых для команды во время выполнения. С помощью этого метода происходит снижение производительности, поскольку ADO необходимо запросить сведения о параметрах источника данных.  
  
 Другие различия между в следующем образце кода и кода в [параметров объекта команд](../../../ado/guide/data/command-object-parameters.md), где параметры были введены вручную. Во-первых, этот код не устанавливает **Готово** свойства **True** , так как он является хранимой процедуры SQL Server и компилируется по определению. Во-вторых, **CommandType** свойство **команда** объект изменен на **adCmdStoredProc** во втором примере для информирования ADO, что команда выполнена хранимая процедура.  
  
 Наконец во втором примере параметр должен называться по индексу при установке значения, поскольку может не знать имя параметра во время разработки. Если известно имя параметра, можно задать новый [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) свойство **команда** объекта значение True и ссылаться на имя свойства. Вы спросите, почему упомянутые позиция первого параметра в хранимую процедуру (@CustomerID)-1 вместо 0 (`objCmd(1) = "ALFKI"`). Это так, как параметр 0 содержит возвращаемое значение хранимой процедуры SQL Server.  
  
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
 [Статья базы знаний 117500](http://go.microsoft.com/fwlink/?LinkId=117500)

