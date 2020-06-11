---
title: Выполнение шаблонов с помощью SQL-запросов (SQLXMLOLEDB)
description: Просмотрите пример клиентского приложения ADO с помощью поставщика SQLXMLOLEDB, чтобы выполнить серверный XML-шаблон, содержащий SQL-запрос.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- templates [SQLXML]
- SQLXMLOLEDB Provider, executing template files
- templates [SQLXML], SQL queries
- XML templates [SQLXML]
- SQL queries [SQLXML]
ms.assetid: ff2bc36f-e3fb-4d8f-8e3a-2680a39eda11
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 82f770d8b17ee1ec93e33efa07b6658363b0de2d
ms.sourcegitcommit: 9921501952147b9ce3e85a1712495d5b3eb13e5b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84215657"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a>Выполнение шаблонов, содержащих SQL-запросы (поставщик SQLXMLOLEDB)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом примере показано использование свойства Клиентсидексмл, зависящего от поставщика SQLXMLOLEDB. В этом образце клиентского приложения ADO на сервере выполняется XML-шаблон, содержащий SQL-запрос.  
  
 Так как свойство Клиентсидексмл имеет значение true, инструкция SELECT без предложения FOR XML отправляется на сервер. Сервер выполняет запрос и возвращает клиенту набор строк. Затем клиент применяет к набору строк преобразование FOR XML и создает XML-документ.  
  
 XML-шаблон предоставляет один корневой элемент верхнего уровня ( \<ROOT> ) для создаваемого XML-документа, поэтому свойство Root XML не предоставляется.  
  
 Для выполнения шаблонов XML должен быть указан диалект {5d531cb2-e6ed-11d2-b252-00c04f681b71}.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения. Кроме того, в этом примере в качестве поставщика данных определено использование собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SQLNCLI11), для которого необходимо установить дополнительное клиентское сетевое ПО. Дополнительные сведения см. в разделе [требования к системе для SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
  
Sub Main()  
  Dim oTestStream As New ADODB.Stream  
  Dim oTestConnection As New ADODB.Connection  
  Dim oTestCommand As New ADODB.Command  
  oTestConnection.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
  
  Set oTestCommand.ActiveConnection = oTestConnection  
  oTestCommand.Properties("ClientSideXML") = True  
  oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:query> " & _  
        "   SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
  oTestStream.Open  
  ' You need the dialect if you are executing   
  ' XML templates (not for SQL queries).  
  oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  oTestCommand.Properties("Output Stream").Value = oTestStream  
  oTestCommand.Execute , , adExecuteStream  
  
  oTestStream.Position = 0  
  oTestStream.Charset = "utf-8"  
  Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
  
Sub Form_Load()  
  Main  
End Sub  
```  
  
  
