---
title: "Использование режима PATH совместно с FOR XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PATH FOR XML, режим"
  - "символы [SQL Server], XML"
  - "псевдонимы [SQL Server], XML"
  - "предложение FOR XML, режим PATH"
  - "PATH FOR XML, режим"
  - "имена столбцов [SQL Server]"
  - "запросы XPath [SQL Server]"
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Использование режима PATH совместно с FOR XML
  Как описано в разделе [Создание XML с помощью предложения FOR XML](../../relational-databases/xml/for-xml-sql-server.md), режим PATH является простым способом смешивания элементов и атрибутов. Режим PATH является также простым способом создания дополнительных вложенных объектов для отражения сложных свойств. Для построения таких XML-документов из набора строк можно использовать запросы FOR XML в режиме EXPLICIT, но режим PATH является более простой альтернативой зачастую громоздким запросам в режиме EXPLICIT. Режим PATH дополнительно к возможности записи вложенных запросов FOR XML и возвращения экземпляров типа **xml** с помощью директивы TYPE позволяет писать менее сложные запросы.  
  
 В режиме PATH имена или псевдонимы столбцов обрабатываются как выражения XPath. Эти выражения показывают, как значения сопоставляются с XML-данными. Каждое выражение на языке XPath является относительным элементом XPath, предоставляющим такие сведения, как атрибут, элемент, скалярное значение, а также имя и иерархию узла, который будет сформирован в связи с элементом строки.  
  
 В этом разделе описано сопоставление столбцов в наборе строк в различных условиях и представлены соответствующие примеры.  
  
## В этом разделе  
  
-   [Столбцы без имени](../../relational-databases/xml/columns-without-a-name.md)  
  
-   [Столбцы с именем](../../relational-databases/xml/columns-with-a-name.md)  
  
-   [Столбцы с именем, заданным в виде символа-шаблона](../../relational-databases/xml/columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [Столбцы с именем XPath-функции проверки узла](../../relational-databases/xml/columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [Имена столбцов с путем, указанным как data()](../../relational-databases/xml/column-names-with-the-path-specified-as-data.md)  
  
-   [Столбцы, по умолчанию содержащие значение NULL](../../relational-databases/xml/columns-that-contain-a-null-value-by-default.md)  
  
-   [Поддержка пространства имен в режиме PATH](../../relational-databases/xml/namespace-support-in-path-mode.md)  
  
-   [Примеры, использование режима PATH](../../relational-databases/xml/examples-using-path-mode.md)  
  
## См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md)  
  
  