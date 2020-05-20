---
title: 'Создание экземпляра события ADO: Visual Basic | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
author: rothja
ms.author: jroth
ms.openlocfilehash: dba3be9c80160dca2773c63b2ed7f7c706678625
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761320"
---
# <a name="ado-event-instantiation-visual-basic"></a>Создание экземпляра события ADO: Visual Basic
Чтобы обеспечить обработку событий ADO в Microsoft® Visual Basic®, необходимо объявить переменную уровня модуля с помощью ключевого слова **WithEvents** . Переменная может быть объявлена только как часть модуля класса и должна быть объявлена на уровне модуля. Однако это не является настолько узким, насколько кажется, поскольку Visual Basic объекты **формы** также являются классами. Самый простой способ обработать события ADO — объявить переменную с помощью **WithEvents**. В следующем примере обрабатывается событие **коннекткомплете** для объекта **Connection** :  
  
```  
' BeginEventExampleVB02  
Dim WithEvents connEvent As Connection  
Attribute connEvent.VB_VarHelpID = -1  
  
Private Sub Form_Load()  
Dim strConn As String  
  
   ' Create a new object with event  
   ' handling enabled.  
   strConn = "Provider=sqloledb;" & _  
      "Data Source=MyServer;" & _  
      "Initial Catalog=Northwind;" & _  
      "Integrated Security=SSPI;"  
   Set connEvent = New ADODB.Connection  
   connEvent.Open strConn  
End Sub  
  
Private Sub connEvent_ConnectComplete(ByVal pError As ADODB.Error, _  
    adStatus As ADODB.EventStatusEnum, _  
    ByVal pConnection As ADODB.Connection)  
Dim strMsg As String  
  
   If adStatus = adStatusErrorsOccurred Then  
      Select Case pError.Number  
         Case adErrOperationCancelled  
            ' The operation was cancelled in the  
            ' Will event. Notify the user and exit.  
            strMsg = "I'm sorry you can't connect right now." & vbCrLf  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
         Case Else  
            strMsg = "Error " & Format(pError.Number) & vbCrLf  
            strMsg = strMsg & pError.Description  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
      End Select  
   End If  
   frmWait.btnOK.Enabled = True  
End Sub  
' EndEventExampleVB02  
```  
  
 Объект **Connection** объявляется на уровне **формы** с помощью ключевого слова **WithEvents** для включения обработки событий. Обработчик событий Form_Load фактически создает объект, назначая новый объект **соединения** для *конневент* , а затем открывает соединение. Конечно, реальное приложение будет выполнять больше обработки в обработчике событий Form_Load, чем показано здесь.
