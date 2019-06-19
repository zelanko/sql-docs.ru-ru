---
title: Вопросы безопасности FOR XML (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34172dcb60e5f2729d8810f697ef975f042f5233
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66010542"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a>Вопросы безопасности FOR XML (SQLXML 4.0)
  Режим FOR XML AUTO создает иерархию XML, в которой имена элементов совпадают с именами таблиц, а имена атрибутов — с именами столбцов. Он предоставляет сведения о таблицах и столбцах базы данных. При использовании режима AUTO (форматирование на стороне сервера) сведения о базе данных можно скрыть, указав в запросе псевдонимы таблиц и столбцов. Эти псевдонимы возвращаются в результирующем XML-документе в виде имен элементов и атрибутов.  
  
 Например, следующий запрос указывает режим AUTO. Таким образом, на сервере выполняется форматирование XML-кода.  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 В результирующем XML-документе псевдонимы используются для имен элементов и атрибутов:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 При использовании режима NESTED (форматирование на стороне клиента) псевдонимы возвращаются только для атрибутов в результирующем XML-документе. Имена базовых таблиц всегда возвращаются в виде имен элементов. Например, следующий запрос указывает режим NESTED.  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 В результирующем XML-документе имена базовых таблиц, возвращаемые в виде имен элементов и псевдонимов таблиц, не используются:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
