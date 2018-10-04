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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0223d4d4346f26ff9339fce3cbc43be9bfcbe82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772482"
---
# <a name="ado-event-instantiation-visual-basic"></a>Создание экземпляра события ADO: Visual Basic
Для обработки событий ADO в Microsoft® Visual Basic, необходимо объявить переменной уровня модуля с помощью **WithEvents** ключевое слово. Переменную можно объявить только как часть класса модуля и должен быть объявлен на уровне модуля. Это не ограничения, поскольку он, тем не менее, так как Visual Basic **формы** объектов также являются классами. — Это самый простой способ обработки событий ADO для объявления переменной с помощью **WithEvents**. В следующем примере показана обработка **ConnectComplete** событие для **подключения** объекта:  
  
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
  
 **Подключения** объект объявляется в **формы** уровня с помощью **WithEvents** ключевое слово, чтобы включить обработку событий. Обработчик событий Form_Load фактически создает объект, присваивание нового **подключения** объект *connEvent* , а затем открывает соединение. Само собой реальное приложение сделать больше операций обработки в обработчик событий Form_Load не показан здесь.
