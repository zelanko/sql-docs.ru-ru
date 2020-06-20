---
title: Использование режима RAW для FOR XML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b2908a98336ec8a6e12029ad471f22a33d7a4dcf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061185"
---
# <a name="use-raw-mode-with-for-xml"></a>Использование с RAW Mode для FOR XML
  Режим RAW преобразует каждую строку в результирующем наборе запроса в XML-элемент с универсальным идентификатором \<row> или при необходимости заданное имя элемента. По умолчанию каждое значение столбца в наборе строк, не равное NULL, сопоставляется с атрибутом \<row> элемента. Если директива ELEMENTs добавляется в предложение FOR XML, то каждое значение столбца сопоставляется с вложенным элементом \<row> элемента. Вместе с директивой ELEMENTS можно дополнительно определить параметр XSINIL для сопоставления значений NULL столбца в результирующем наборе с элементом, обладающим атрибутом xsi:nil=`"`true`"`.  
  
 Есть возможность сделать запрос схемы итогового XML. При определении параметра XMLDATA возвращается встроенная схема XDR. При задании параметра XMLSCHEMA возвращается встроенная XSD-схема. Схема появляется в начале данных. В итоге ссылка на пространство имен схемы будет повторяться для каждого элемента высшего уровня.  
  
 Параметр BINARY BASE64 необходимо определить в предложении FOR XML для возвращения двоичных данных в base64-кодированном формате. В режиме RAW извлечение двоичных данных без определения параметра BINARY BASE64 приводит к ошибке.  
  
## <a name="in-this-section"></a>в этом разделе  
 Этот раздел содержит следующие примеры.  
  
-   [Пример. Получение сведений о модели продукта в формате XML](example-retrieving-product-model-information-as-xml.md)  
  
-   [Пример. Указание XSINIL с директивой ELEMENTS](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Пример Запросы к схемам как к результатам с помощью параметров XMLDATA и XMLSCHEMA](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Пример. Получение двоичных данных](example-retrieving-binary-data.md)  
  
-   [Пример. Переименование элемента &#60;row&#62;](example-renaming-the-row-element.md)  
  
-   [Пример. Задание корневого элемента для XML-документа, сформированного предложением FOR XML](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Пример. Запросы к столбцам XMLType](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Использование режима AUTO совместно с FOR XML](use-auto-mode-with-for-xml.md)   
 [Использование режима EXPLICIT совместно с предложением FOR XML](use-explicit-mode-with-for-xml.md)   
 [Использование режима PATH совместно с FOR XML](use-path-mode-with-for-xml.md)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML (SQL Server)](../xml/for-xml-sql-server.md)  
  
  
