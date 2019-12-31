---
title: Форматирование XML на стороне сервера (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ec84fdfad468124f59cefde73486d5b19a5a4110
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75255902"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Форматирование XML-кода на сервере (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе содержится информация о форматировании на серверной стороне XML-документов из наборов строк, которые создаются при выполнении запросов к базе данных в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно помещать XML-документы в таблицы базы данных и получать XML-документы из них. Для получения XML-документа в запросе SELECT используется расширение FOR XML.  
  
 Например, предположим, что клиентское приложение выполняет команду [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , состоящую из следующего [!INCLUDE[tsql](../../../includes/tsql-md.md)] запроса:  
  
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
  
-   AUTO (АВТОМАТИЧЕСКИ)  
  
-   EXPLICIT  
  
 Дополнительные сведения о предложении FOR XML см. в разделе [Создание XML с помощью предложения FOR XML](../../../relational-databases/xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура форматирования XML на стороне клиента и на стороне сервера &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Форматирование XML на стороне клиента &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [ДЛЯ SQL Server &#40;XML&#41;](../../../relational-databases/xml/for-xml-sql-server.md)  
  
  
