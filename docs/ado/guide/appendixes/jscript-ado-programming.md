---
title: "Программирование ADO JScript | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6ae8137c2e5641594c3ddcf768c47b7fe844fafc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="jscript-ado-programming"></a>Программирование ADO JScript
## <a name="creating-an-ado-project"></a>Создание проекта ADO  
 Microsoft JScript не поддерживает библиотеки типов, поэтому вам не нужно ссылки ADO в своем проекте. Следовательно не связанные функции, такие как завершение командной строки поддерживаются. Кроме того по умолчанию ADO перечисляемые константы не определены в языке JScript.  
  
 Тем не менее ADO предоставляет с двумя включить файлы, содержащие следующие определения, используемые в JScript:  
  
-   Для использования серверных скриптов Adojavas.inc, которая устанавливается в папках библиотеки ADO.  
  
-   Для использования клиентского скрипта Adcjavas.inc, которая устанавливается в папках библиотеки ADO.  
  
 Можно либо скопировать и вставить определения констант из этих файлов в ASP-страниц или, при выполнении скриптов на стороне сервера, скопируйте файл Adojavas.inc в папку на веб-сайте и ссылается на его со страницы ASP следующим образом:  
  
```  
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Создание объектов ADO в JScript  
 Вместо этого необходимо использовать **CreateObject** вызов функции:  
  
```  
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>Пример JScript  
 Ниже приведен общий пример программирования на стороне сервера JScript в открывшемся файле активные страницы сервера (ASP) **записей** объекта:  
  
```  
<%  @LANGUAGE="JScript" %>  
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
