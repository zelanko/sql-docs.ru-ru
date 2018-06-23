---
title: Использование режима PATH для FOR XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
caps.latest.revision: 44
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e184fc7502af6174eef5cac8cd2914737841bb7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180215"
---
# <a name="use-path-mode-with-for-xml"></a>Использование режима PATH совместно с FOR XML
  Как описано в разделе [Создание XML с помощью предложения FOR XML](for-xml-sql-server.md), режим PATH является простым способом смешивания элементов и атрибутов. Режим PATH является также простым способом создания дополнительных вложенных объектов для отражения сложных свойств. Для построения таких XML-документов из набора строк можно использовать запросы FOR XML в режиме EXPLICIT, но режим PATH является более простой альтернативой зачастую громоздким запросам в режиме EXPLICIT. Режим PATH дополнительно к возможности записи вложенных запросов FOR XML и возвращения экземпляров типа **xml** с помощью директивы TYPE позволяет писать менее сложные запросы.  
  
 В режиме PATH имена или псевдонимы столбцов обрабатываются как выражения XPath. Эти выражения показывают, как значения сопоставляются с XML-данными. Каждое выражение на языке XPath является относительным элементом XPath, предоставляющим такие сведения, как атрибут, элемент, скалярное значение, а также имя и иерархию узла, который будет сформирован в связи с элементом строки.  
  
 В этом разделе описано сопоставление столбцов в наборе строк в различных условиях и представлены соответствующие примеры.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Столбцы без имени](columns-without-a-name.md)  
  
-   [Столбцы с именем](columns-with-a-name.md)  
  
-   [Столбцы с именем, заданным в виде символа-шаблона](columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [Столбцы с именем XPath-функции проверки узла](columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [Имена столбцов с путем, указанным как data()](column-names-with-the-path-specified-as-data.md)  
  
-   [Столбцы, по умолчанию содержащие значение NULL](columns-that-contain-a-null-value-by-default.md)  
  
-   [Поддержка пространства имен в режиме PATH](namespace-support-in-path-mode.md)  
  
-   [Примеры, использование режима PATH](examples-using-path-mode.md)  
  
## <a name="see-also"></a>См. также  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML (SQL Server)](for-xml-sql-server.md)  
  
  
