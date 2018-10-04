---
title: Выполнение запросов SQL (поставщик SQLXMLOLEDB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXMLOLEDB Provider
- xml root property [SQLXML]
- SQLXMLOLEDB Provider, executing SQL queries
- SQL queries [SQLXML]
ms.assetid: 50334cf5-9c87-4c00-9beb-e08577c4fa82
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0bf453deb98b060e799a52995a0dd45f00e5b9a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095424"
---
# <a name="executing-sql-queries-sqlxmloledb-provider"></a>Выполнение запросов SQL (поставщик SQLXMLOLEDB)
  Этот пример показывает использование следующих свойств SQLXMLOLEDB, определяемых поставщиком.  
  
-   ClientSideXML  
  
-   xml root  
  
 В этом образце клиентского приложения ADO на стороне клиента выполняется простой SQL-запрос. Так как ClientSideXML, свойство имеет значение True, на сервер отправляется инструкция SELECT без предложения FOR XML. Сервер выполняет запрос и возвращает клиенту набор строк. Затем клиент применяет к набору строк преобразование FOR XML и создает XML-документ.  
  
 Корневое свойство xml предоставляет единый корневой элемент для XML-документа, который создается.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения. Кроме того, в данном примере задается использование собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SQLNCLI11) для поставщика данных, для которого необходимо установить дополнительное клиентское сетевое ПО. Дополнительные сведения см. в разделе [требования к системе для собственного клиента SQL Server](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI ;"  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = "SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO"  
oTestStream.Open  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("xml root") = "root"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
