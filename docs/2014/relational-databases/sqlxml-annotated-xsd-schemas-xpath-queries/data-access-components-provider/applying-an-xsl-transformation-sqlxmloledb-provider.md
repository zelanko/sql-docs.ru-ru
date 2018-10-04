---
title: Применение преобразования XSL (поставщик SQLXMLOLEDB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 11f7ce945dcf4b89c6b76ba14e0383bc38ca3c39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224044"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a>Применение преобразования XSL (поставщик SQLXMLOLEDB)
  В этом образце приложения ADO выполняется SQL-запрос, и к результату применяется преобразование XSL. ClientSideXML свойству присвоено значение True, обеспечивает обработку набора строк на стороне клиента. Диалект команды имеет значение {5d531cb2-e6ed-11d2-b252-00c04f681b71}, поскольку SQL-запрос задан в шаблоне, а при выполнении шаблона должен указываться этот диалект. Свойство xsl задает XSL-файл, использовать для применения преобразования. Значение свойства базовый путь используется для поиска XSL-файл. Если путь указан в значении свойства xsl, путь задается относительно пути, указанного в свойстве базовый путь.  
  
 В этом примере показано, как использовать следующие свойства, определяемые поставщиком SQLXMLOLEDB.  
  
-   ClientSideXML  
  
-   xsl  
  
 В этом образце клиентского приложения ADO на сервере выполняется XML-шаблон, содержащий SQL-запрос.  
  
 Так как ClientSideXML, свойство имеет значение True, на сервер отправляется инструкция SELECT без предложения FOR XML. Сервер выполняет запрос и возвращает клиенту набор строк. Затем клиент применяет к набору строк преобразование FOR XML и создает XML-документ.  
  
 Свойство xsl задается в приложении; Таким образом преобразование XSL применяется к XML-документ, который создается на стороне клиента, и результатом является таблица двух столбцов.  
  
 Для выполнения этой команды шаблона необходимо указать диалект XML-шаблона {5d531cb2-e6ed-11d2-b252-00c04f681b71}.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения. Кроме того, в данном примере указано использование собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве поставщика данных, для чего требуется установка дополнительного клиентского сетевого ПО. Дополнительные сведения см. в разделе [требования к системе для собственного клиента SQL Server](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 Ниже приведен XSL-шаблон. Результатом его применения является таблица из двух столбцов.  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
