---
title: Обработка ошибок в VBScript | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- VBScript error handling [ADO]
- errors [ADO], VBScript
ms.assetid: 31bc3743-32d3-4bc7-ac61-ee6ed0fdec70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 99c3d2a615abe64a6ea5fc79cab8fb3dc083178d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925143"
---
# <a name="handling-errors-in-vbscript"></a>Обработка ошибок в VBScript
Есть небольшая разница в методы, используемые в Visual Basic и тех, которые используются с VBScript. Основное различие заключается в том, что VBScript не поддерживает концепцию обработку ошибок, выполнение продолжается на метки. Другими словами, нельзя использовать `On Error GoTo` в VBScript. Вместо этого используйте `On Error Resume Next` и затем выберите оба варианта **Err.Number** и **число** свойство **ошибки** коллекции, как показано в следующем примере:  
  
```  
<!-- BeginErrorExampleVBS -->  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<TITLE>Error Handling Example (VBScript)</TITLE>  
</HEAD>  
<BODY>  
  
<h1>Error Handling Example (VBScript)</h1>  
  
<%  
  
   Dim cnn1  
   Dim errLoop  
   Dim strError  
  
   On Error Resume Next  
  
   ' Intentionally trigger an error.  
   Set cnn1 = Server.CreateObject("ADODB.Connection")  
   cnn1.Open "nothing"  
  
   If cnn1.Errors.Count > 0 Then  
      ' Enumerate Errors collection and display  
      ' properties of each Error object.  
      For Each errLoop In cnn1.Errors  
         strError = "Error #" & errLoop.Number & "<br>" & _  
            "   " & errLoop.Description & "<br>" & _  
            "   (Source: " & errLoop.Source & ")" & "<br>" & _  
            "   (SQL State: " & errLoop.SQLState & ")" & "<br>" & _  
            "   (NativeError: " & errLoop.NativeError & ")" & "<br>"  
         If errLoop.HelpFile = "" Then  
            strError = strError & _  
               "   No Help file available" & _  
               "<br><br>"  
         Else  
            strError = strError & _  
               "   (HelpFile: " & errLoop.HelpFile & ")" & "<br>" & _  
               "   (HelpContext: " & errLoop.HelpContext & ")" & _  
               "<br><br>"  
         End If  
  
         Response.Write("<p>" & strError & "</p>")  
      Next  
   End If  
  
%>  
  
</BODY>  
</HTML>  
<!-- EndErrorExampleVBS -->  
```
