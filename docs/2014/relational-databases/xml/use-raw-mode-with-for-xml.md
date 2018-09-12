---
title: Использование режима RAW для FOR XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 001c06b44eba66bd7e1ee1da3907d39158d5d4ce
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890230"
---
# <a name="use-raw-mode-with-for-xml"></a>Использование с RAW Mode для FOR XML
  Режим RAW преобразует каждую строку из результирующего набора запроса в элемент XML и присваивает ему универсальный идентификатор \<row> или необязательное имя элемента. По умолчанию каждое значение столбца в наборе строк, отличное от NULL, сопоставляется с определенным атрибутом элемента \<row>. Если директива ELEMENTS добавляется в предложение FOR XML, то каждому значению столбца сопоставляется дочерний элемент элемента \<row>. Вместе с директивой ELEMENTS можно дополнительно определить параметр XSINIL для сопоставления значений NULL столбца в результирующем наборе с элементом, обладающим атрибутом xsi:nil=`"`true`"`.  
  
 Есть возможность сделать запрос схемы итогового XML. При определении параметра XMLDATA возвращается встроенная схема XDR. При задании параметра XMLSCHEMA возвращается встроенная XSD-схема. Схема появляется в начале данных. В итоге ссылка на пространство имен схемы будет повторяться для каждого элемента высшего уровня.  
  
 Параметр BINARY BASE64 необходимо определить в предложении FOR XML для возвращения двоичных данных в base64-кодированном формате. В режиме RAW извлечение двоичных данных без определения параметра BINARY BASE64 приводит к ошибке.  
  
## <a name="in-this-section"></a>в этом разделе  
 Этот раздел содержит следующие примеры.  
  
-   [Пример. Получение сведений о модели продукта в формате XML](example-retrieving-product-model-information-as-xml.md)  
  
-   [Пример. Указание XSINIL с директивой ELEMENTS](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Пример: запросы к схемам как к результатам с помощью параметров XMLDATA и XMLSCHEMA](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Пример. Получение двоичных данных](example-retrieving-binary-data.md)  
  
-   [Пример. Переименование элемента &#60;row&#62;](example-renaming-the-row-element.md)  
  
-   [Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Пример. Запросы к столбцам XMLType](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>См. также  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Использование режима AUTO совместно с FOR XML](use-auto-mode-with-for-xml.md)   
 [Использование режима EXPLICIT совместно с предложением FOR XML](use-explicit-mode-with-for-xml.md)   
 [Использование с PATH Mode для FOR XML](use-path-mode-with-for-xml.md)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML (SQL Server)](../xml/for-xml-sql-server.md)  
  
  
