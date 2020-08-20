---
description: Программирование объектов ADO с использованием VBScript
title: Программирование на языке сценариев VBScript | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 8bea576e55537d2b4ee75fb8e7a0fcdebea4847e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453966"
---
# <a name="vbscript-ado-programming"></a>Программирование объектов ADO с использованием VBScript
## <a name="creating-an-ado-project"></a>Создание проекта ADO  
 Microsoft Visual Basic, Scripting Edition не поддерживает библиотеки типов, поэтому вам не нужно ссылаться на ADO в проекте. Следовательно, связанные компоненты, такие как завершение командной строки, не поддерживаются. Кроме того, по умолчанию перечислимые константы ADO не определяются в VBScript.  
  
 Однако ADO предоставляет два включаемых файла, содержащие следующие определения для использования с VBScript:  
  
-   Для сценариев на стороне сервера используйте Адовбс. Inc, который по умолчанию устанавливается в папку c:\Program Files\Common Филес\систем\адо\.  
  
-   Для сценариев на стороне клиента используйте Адквбс. Inc, который по умолчанию устанавливается в папку c:\Program Files\Common Филес\систем\мсдак\.  
  
 Можно скопировать и вставить константные определения из этих файлов в страницы ASP или, если вы выполняете скрипт на стороне сервера, скопировать файл Адовбс. Inc в папку на веб-сайте и ссылаться на него со страницы ASP следующим образом:  
  
```vb
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Создание объектов ADO в VBScript  
 Нельзя использовать оператор **Dim** для назначения объектов конкретному типу в VBScript. Кроме того, VBScript не поддерживает **Новый** синтаксис, используемый с инструкцией **Dim** в Visual Basic для приложений. Вместо этого следует использовать вызов функции **CreateObject** :  
  
```vb
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Примеры VBScript  
 Следующий код является универсальным примером программирования на стороне сервера VBScript в файле Active Server страницы (ASP):  
  
```vb
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 Более конкретные примеры VBScript включены в документацию по ADO. Дополнительные сведения см. [в статье примеры кода ADO в Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Различия между VBScript и Visual Basic  
 Использование ADO с VBScript аналогично использованию ADO с Visual Basic различными способами, включая использование синтаксиса. Однако существуют некоторые существенные отличия.  
  
-   VBScript поддерживает только тип данных Variant, который может содержать различные типы данных. Вы можете хранить нужные данные в типе данных Variant, и данные будут работать надлежащим образом из-за приведения, выполняемого VBScript. Он распознает тип, необходимый для ADO, и соответствующим образом преобразует значение в варианте.  
  
-   Нельзя использовать **On Error GoTo \<label> ** в VBScript.  
  
-   VBScript поддерживает некоторые встроенные функции Visual Basic, такие как **MsgBox**, **Date**и **ISNUMERIC**. Однако поскольку VBScript является подмножеством Visual Basic, поддерживаются не все встроенные функции. Например, VBScript не поддерживает функцию **Format** и функции файлового ввода-вывода.
