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
ms.openlocfilehash: 2f0c76a668c7191467e9f66ba48c486aceea16df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924348"
---
# <a name="retrieving-resultsets-into-streams"></a>Извлечение результирующих наборов в потоки
Вместо того чтобы получать результаты в традиционном объекте **Recordset** , ADO может получить результаты запроса в потоке. Объект **потока** ADO (или другие объекты, поддерживающие интерфейс **IStream** com, например объекты **запросов** и **ответов** ASP) можно использовать для хранения этих результатов. Одним из способов использования этой функции является получение результатов в формате XML. С SQL Server, например, результаты XML могут возвращаться несколькими способами, например с помощью предложения FOR XML с запросом SQL SELECT или с помощью запроса XPath.  
  
 Чтобы получить результаты запроса в формате потока, а не в **наборе записей**, необходимо указать константу **адексекутестреам** из **Ексекутеоптионенум** в качестве параметра метода **EXECUTE** объекта **Command** . Если поставщик поддерживает эту функцию, результаты будут возвращены в поток после выполнения. Перед выполнением кода может потребоваться указать дополнительные свойства, зависящие от поставщика. Например, при использовании поставщика Microsoft OLE DB для SQL Server свойства, такие как **выходной поток** в коллекции **Properties** объекта **Command** , должны быть указаны. Дополнительные сведения о связанных с этой функцией динамических свойствах SQL Server см. в разделе Свойства, связанные с XML, в электронная документация на SQL Server.  
  
## <a name="for-xml-query-example"></a>Пример запроса FOR XML  
 Следующий пример написан на языке VBScript в базе данных Northwind:  
  
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
  
 Предложение FOR XML указывает SQL Server вернуть данные в виде XML-документа.  
  
### <a name="for-xml-syntax"></a>Синтаксис FOR XML  
  
```syntax
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 FOR XML RAW создает универсальные элементы строки, имеющие значения столбцов в качестве атрибутов. FOR XML AUTO использует эвристику для создания иерархического дерева с именами элементов на основе имен таблиц. FOR XML EXPLICIT создает универсальную таблицу со связями, полностью описываемыми метаданными.  
  
 Ниже приведен пример инструкции SQL SELECT FOR XML.  
  
```sql
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 Команда может быть указана в строке, как показано выше, назначена **CommandText**, или в форме запроса к XML-шаблону, назначенного **CommandStream**. Дополнительные сведения о запросах XML-шаблонов см. в разделе [потоки команд](../../../ado/guide/data/command-streams.md) в ADO или использование потоков для ввода команды в Электронная документация на SQL Server.  
  
 Как запрос шаблона XML, запрос FOR XML выглядит следующим образом:  
  
```xml
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 В этом примере указывается объект **ответа** ASP для свойства **потока вывода** :  
  
```vb
adoCmd.Properties("Output Stream") = Response  
```  
  
 Затем укажите параметр **адексекутестреам** командлета **EXECUTE**. В этом примере поток переносится в XML-теги, чтобы создать остров данных XML:  
  
```vb
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>Remarks  
 На этом этапе XML передается в браузер клиента и готов к отображению. Это делается с помощью сценария VBScript на стороне клиента для привязки XML-документа к экземпляру модели DOM и циклической обработки каждого дочернего узла для создания списка продуктов в формате HTML.
