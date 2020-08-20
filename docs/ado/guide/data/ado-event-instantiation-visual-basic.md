---
description: 'Создание экземпляра события ADO: Visual Basic'
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
ms.openlocfilehash: 1ea53b5d48c0eb72fe91ebeda2d2612437cf4c36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453796"
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
