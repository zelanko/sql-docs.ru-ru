---
title: Программирование ADO на JScript | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d07759405dc337667cc8971ce7795af428a0cfa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926801"
---
# <a name="jscript-ado-programming"></a>Программирование объектов ADO с использованием JScript
## <a name="creating-an-ado-project"></a>Создание проекта ADO  
 Microsoft JScript не поддерживает библиотеки типов, поэтому вам не нужно ссылаться на ADO в проекте. Следовательно, связанные компоненты, такие как завершение командной строки, не поддерживаются. Кроме того, по умолчанию перечислимые константы ADO не определяются в JScript.  
  
 Однако ADO предоставляет два включаемых файла, содержащие следующие определения для использования с JScript:  
  
-   Для сценариев на стороне сервера используйте Адожавас. Inc, установленный в папках библиотеки ADO.  
  
-   Для сценариев на стороне клиента используйте Адкжавас. Inc, установленный в папках библиотеки ADO.  
  
 Можно скопировать и вставить константные определения из этих файлов в страницы ASP, или, если вы выполняете скрипт на стороне сервера, скопируйте файл Адожавас. Inc в папку на веб-сайте и обращаетесь к нему со страницы ASP следующим образом:  
  
```javascript
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Создание объектов ADO в JScript  
 Вместо этого следует использовать вызов функции **CreateObject** :  
  
```javascript
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>Пример JScript  
 Следующий код является универсальным примером программирования на стороне сервера JScript в файле Active Server Page (ASP), открывающем объект **Recordset** :  
  
```javascript
<%  @LANGUAGE="JScript" %>  
<!--#include File="adojavas.inc"-->  
<HTML>  
<BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
<%  
var Source = "SELECT * FROM Authors";  
var Connect =  "Provider=sqloledb;Data Source=srv;" +  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );  
Rs1.Open(Source,Connect,adOpenForwardOnly);  
Response.Write("Success!");  
%>  
</BODY>  
</HTML>  
```
