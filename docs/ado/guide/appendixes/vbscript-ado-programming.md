---
title: Программирование ADO для VBScript | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a2b6172fdd35e98d1b4a5f1b3c6ff19293a7f81
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214685"
---
# <a name="vbscript-ado-programming"></a>Программирование объектов ADO с использованием VBScript
## <a name="creating-an-ado-project"></a>Создание проекта ADO  
 Microsoft Visual Basic, Scripting Edition не поддерживает библиотеки типов, поэтому вы не обязательно должны ссылаться на ADO в проекте. Следовательно не связанные функции, такие как завершение командной строки, поддерживаются. Кроме того по умолчанию ADO перечисления константы не определены в VBScript.  
  
 Тем не менее ADO предоставляет с двумя включить файлы, содержащие следующие определения для использования с VBScript:  
  
-   Для использования сценариев на стороне сервера Adovbs.inc установленный в папке c:\Program Files\Common Files\System\ado\ по умолчанию.  
  
-   Для использования сценариев на стороне клиента Adcvbs.inc установленный в папке c:\Program Files\Common Files\System\msdac\ по умолчанию.  
  
 Можно скопировать и вставить определения констант из этих файлов в ASP-страниц или, при выполнении сценариев на стороне сервера, скопируйте файл Adovbs.inc в папку на веб-сайт и ссылок из ASP-страницы следующим образом:  
  
```vb
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Создание объектов ADO в VBScript  
 Нельзя использовать **Dim** инструкцию, чтобы назначить объекты конкретного типа в VBScript. Кроме того, не поддерживает VBScript **New** синтаксис, используемый с **Dim** в Visual Basic для приложений. Вместо этого необходимо использовать **CreateObject** вызов функции:  
  
```vb
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Примеры VBScript  
 Ниже приведен общий пример программирования на стороне сервера VBScript в файле Active Server Page (ASP).  
  
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
  
 Подробные примеры VBScript входят в состав документации по объектам ADO. Дополнительные сведения см. в разделе [примеры кода ADO в Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Различия между VBScript и Visual Basic  
 Использование ADO с VBScript похоже на использование ADO с помощью Visual Basic разными способами, включая использование синтаксиса. Тем не менее существует ряд существенных отличий:  
  
-   VBScript поддерживает только тип данных Variant, который может хранить различные типы данных. Необходимые данные можно хранить в тип данных Variant, и данные будут работать неправильно из-за приведения, выполненных VBScript. Он распознает этот тип, необходимый ADO и соответствующим образом преобразует значение в тип Variant.  
  
-   Нельзя использовать **на goto ошибка \<label >** в VBScript.  
  
-   VBScript поддерживает некоторые встроенные функции Visual Basic, такие как **Msgbox**, **даты**, и **IsNumeric**. Тем не менее так как VBScript — это подмножество Visual Basic, поддерживаются не все встроенные функции. Например, VBScript не поддерживает **формат** функции и функций файлового ввода-вывода.
