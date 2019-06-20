---
title: Извлечение результирующих наборов в потоки | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO], retrieving query results
- query results into stream [ADO]
- retrieving results into stream [ADO]
ms.assetid: 996c1321-c926-4f57-8297-85c8c20de974
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b784553302bf9df30750f239291ca179ecf6cf74
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701877"
---
# <a name="retrieving-resultsets-into-streams"></a>Извлечение результирующих наборов в потоки
Вместо получения результатов в традиционных **записей** объекта ADO вместо этого можно получить результаты запроса в поток. ADO **Stream** объекта (или другим объектом, поддерживающим COM- **IStream** интерфейса, например ASP **запроса** и **ответа** объектов ) можно использовать для хранения этих результатов. Эта функция применяется для получения результатов в формате XML. С помощью SQL Server, например, XML результаты могут быть возвращены несколькими способами, например с помощью предложения FOR XML с помощью SQL-запрос SELECT или с помощью запроса XPath.  
  
 Для получения результатов запроса в формате потока, а не в **записей**, необходимо указать **adExecuteStream** константы из **ExecuteOptionEnum** как параметр **Execute** метод **команда** объекта. Если поставщик поддерживает эту функцию, результаты возвращаются в поток после выполнения. Может потребоваться указать дополнительные свойства поставщика, до выполнения кода. Например, с помощью поставщика Microsoft OLE DB для SQL Server, свойства, такие как **выходные данные Stream** в **свойства** коллекцию **команда** объект должен быть указан. Дополнительные сведения о динамических свойствах конкретного сервера SQL, связанное с данной возможностью см. в разделе свойств XML-Related в SQL Server Books Online.  
  
## <a name="for-xml-query-example"></a>Пример запросов XML  
 Следующий пример написан на языке VBScript в базу данных Northwind:  
  
```html
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<%  Option Explicit      %>  
  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=" & _  
      Request.ServerVariables("SERVER_NAME") & ";" & _  
      Initial Catalog=Northwind;Integrated Security=SSPI;"  
  
   Response.write "Connect String = " & sConn & "<BR/>"  
  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
  
   adoConn.Open  
  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT * FROM PRODUCTS WHERE ProductName='Gumbr Gummibrchen' FOR XML AUTO</sql:query></ROOT>"  
  
   Response.write "Query String = " & sQuery & "<BR/>"  
  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
  
%>  
  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   xmlDoc.resolveExternals=false  
   xmlDoc.async=false  
  
   If xmlDoc.parseError.Reason <> "" then  
      Msgbox "parseError.Reason = " & xmlDoc.parseError.Reason  
   End If  
  
   Dim root, child  
   Set root = xmlDoc.documentElement  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI>" & child.getAttribute("ProductName") & "</LI>"  
   Next  
</SCRIPT>  
  
</HEAD>  
  
<BODY>  
  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
  
```  
  
 Предложение FOR XML указывает, что SQL Server для возврата данных в виде XML-документа.  
  
### <a name="for-xml-syntax"></a>ДЛЯ XML-синтаксис  
  
```syntax
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 ДЛЯ XML RAW создает универсальный строки элементов, которые имеют значения столбцов как атрибуты. Для FOR XML AUTO использует эвристику для создания иерархического дерева с именами элементов, на основе имен таблиц. FOR XML EXPLICIT создает универсальной таблицы со связями, полностью описаны в метаданных.  
  
 Ниже приводится пример инструкции SELECT SQL FOR XML:  
  
```sql
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 Команда может указать в строке, как показано выше, назначенным **CommandText**, или в виде XML-шаблон запрос назначен **CommandStream**. Дополнительные сведения о запросах шаблон XML, см. в разделе [команды потоки](../../../ado/guide/data/command-streams.md) в ADO или использование потоков для ввода команды в SQL Server Books Online.  
  
 Как шаблон XML-запрос запрос FOR XML выглядит следующим образом:  
  
```xml
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 В этом примере указывается ASP **ответа** для объекта **выходные данные Stream** свойство:  
  
```vb
adoCmd.Properties("Output Stream") = Response  
```  
  
 Затем укажите **adExecuteStream** параметр **Execute**. В этом примере создает оболочку для потока в XML-теги для создания острова данных XML:  
  
```vb
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>Примечания  
 На этом этапе XML передан в браузер клиента, и она готова для отображения. Это делается с помощью VBScript на стороне клиента для доступа к XML-документ экземпляра модели DOM и циклически каждого дочернего узла, для построения списка продуктов в формате HTML.
