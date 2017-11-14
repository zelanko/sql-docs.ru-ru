---
title: "Получение результирующих наборов в потоки | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streams [ADO], retrieving query results
- query results into stream [ADO]
- retrieving results into stream [ADO]
ms.assetid: 996c1321-c926-4f57-8297-85c8c20de974
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9aadb2a81cc93effa0c280f5f74e6403c7403756
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-resultsets-into-streams"></a>Получение результирующих наборов в потоки
Вместо получения результатов в традиционных **записей** объекта ADO вместо этого можно получить результаты запроса в поток. ADO **поток** объекта (или другие объекты, которые поддерживают COM **IStream** интерфейса, таких как ASP **запроса** и **ответ** объектов ) можно использовать для хранения этих результатов. Эта возможность применяется для получения результатов в формате XML. С SQL Server например, XML-результатов могут быть возвращены несколькими способами, например с помощью предложения FOR XML с помощью запроса SELECT языка SQL или с помощью запроса XPath.  
  
 Для получения результатов запроса в формате потока, а не в **записей**, необходимо указать **adExecuteStream** константы из **ExecuteOptionEnum** как параметр **Execute** метод **команда** объекта. Если поставщик поддерживает эту функцию, результаты будут возвращены в поток после выполнения. Может потребоваться указать дополнительные свойства от поставщика, до начала выполнения кода. Например, с помощью поставщика Microsoft OLE DB для SQL Server, свойств, таких как **выходной поток** в **свойства** коллекцию **команда** объект должен быть указано. Дополнительные сведения о динамических свойствах связанные с SQL Server, относящиеся к этой функции см. в разделе свойств XML-Related в электронной документации по SQL Server.  
  
## <a name="for-xml-query-example"></a>Пример запроса XML  
 Следующий пример написан на языке VBScript для базы данных Northwind:  
  
```  
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
  
### <a name="for-xml-syntax"></a>СИНТАКСИС XML  
  
```  
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 XML RAW СОЗДАЕТ универсальный строк элементов, имеющих значения столбцов в качестве атрибутов. FOR XML AUTO использует эвристику для создания иерархического дерева с именами элементов на основе имен таблиц. FOR XML EXPLICIT приводит к возникновению ошибки универсальной таблицы со связями, полностью описаны в метаданных.  
  
 Ниже приведен пример инструкции SELECT SQL FOR XML:  
  
```  
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 Команда может указать в строке, как показано выше, назначенным **CommandText**, или в виде XML-шаблон запроса, назначенный **CommandStream**. Дополнительные сведения о запросах шаблона XML см. в разделе [команда потоки](../../../ado/guide/data/command-streams.md) в ADO или использование потоков для ввода команды в SQL Server Books Online.  
  
 Как шаблон XML-запрос запрос FOR XML выглядит следующим образом:  
  
```  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 В этом примере указывается ASP **ответ** для объекта **выходной поток** свойство:  
  
```  
adoCmd.Properties("Output Stream") = Response  
```  
  
 Затем укажите **adExecuteStream** параметр **Execute**. Этот пример создает оболочку для потока в XML-теги для создания острова данных XML:  
  
```  
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>Замечания  
 На этом этапе XML передан в браузере клиента, и она готова для отображения. Для этого с помощью VBScript на стороне клиента для привязки XML-документ с экземпляром DOM и циклически каждого дочернего узла, для построения списка продуктов в формате HTML.

