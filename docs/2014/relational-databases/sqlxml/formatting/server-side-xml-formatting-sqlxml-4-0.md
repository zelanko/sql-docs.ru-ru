---
title: Форматирование XML на стороне сервера (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af44d854ba28e8e8ac3b1a4572bf9b222f20299b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66012213"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Форматирование XML-кода на сервере (SQLXML 4.0)
  В этом разделе содержится информация о форматировании на серверной стороне XML-документов из наборов строк, которые создаются при выполнении запросов к базе данных в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно помещать XML-документы в таблицы базы данных и получать XML-документы из них. Для получения XML-документа в запросе SELECT используется расширение FOR XML.  
  
 Предположим, например, клиентское приложение выполняет команду в отношении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , состоит из следующих [!INCLUDE[tsql](../../../includes/tsql-md.md)] запроса:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 Сервер выполняет запрос в два шага. Во-первых, сервер выполняет следующую инструкцию SELECT:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Затем сервер применяет преобразование FOR XML к сформированному набору строк. Результирующий XML-документ затем отправляется клиенту в виде набора строк, состоящего из одного столбца. В данной документации этот процесс называется форматированием XML на стороне сервера.  
  
 На стороне сервера можно указать следующие режимы при помощи предложения FOR XML:  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 Дополнительные сведения о предложении FOR XML, см. в разделе [конструирование XML используя FOR XML](../../xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура форматирования XML, клиентские и серверные &#40;SQLXML 4.0&#41;](architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Форматирование XML на стороне клиента &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML (SQL Server)](../../xml/for-xml-sql-server.md)  
  
  
