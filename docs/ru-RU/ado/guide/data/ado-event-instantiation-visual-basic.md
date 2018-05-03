---
title: 'При создании экземпляра события ADO: Visual Basic | Документы Microsoft'
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91452f6f087cde82878a5478707f538fff284db5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ado-event-instantiation-visual-basic"></a>При создании экземпляра события ADO: Visual Basic
Чтобы обработать события ADO в Microsoft® Visual Basic, необходимо объявить переменной уровня модуля с помощью **WithEvents** ключевое слово. Переменная может быть объявлен только как часть класса модуля и должен быть объявлен на уровне модуля. Это же ограничения, как кажется, однако из-за Visual Basic **формы** объектов также являются классами. Самый простой способ обработки событий ADO — объявить переменную с помощью **WithEvents**. В следующем примере показана обработка **ConnectComplete** событий для **подключения** объекта:  
  
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
  
 **Подключения** объект объявляется в **формы** уровня с помощью **WithEvents** ключевое слово, чтобы включить обработку событий. Обработчик событий Form_Load фактически создает объект путем назначения нового **подключения** объект *connEvent* , а затем открывает соединение. Конечно реальному приложению может потребоваться дополнительной обработки в обработчике событий Form_Load, чем показано здесь.
