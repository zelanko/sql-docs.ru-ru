---
title: Аннотации XSD (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b9e50cc418ef1fa2076b3207d7d3429694f160a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013548"
---
# <a name="xsd-annotations-sqlxml-40"></a>Заметки XSD (SQLXML 4.0)
  В таблице перечисляются заметки XSD, введенные в версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и проводится их сравнение с заметками XDR, введенными в версии [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Заметка XSD|Description|Ссылка на раздел|Заметка XDR|  
|--------------------|-----------------|----------------|--------------------|  
|`sql:encode`|Позволяет запросить URI-ссылку, когда элемент или атрибут XML сопоставлен с BLOB-столбцом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью этой URI-ссылки можно потом возвратить данные типа BLOB.|[Запрос URL-ссылок на данные большого двоичного объекта с помощью SQL: Encoded &#40;SQLXML 4,0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|`url-encode`|  
|`sql:guid`|Позволяет указать, нужно ли использовать значение идентификатора GUID, созданное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или значение, заданное в диаграмме обновления для данного столбца.|[Использование заметок sql:identity и sql:guid](using-the-sql-identity-and-sql-guid-annotations.md)|Не поддерживается|  
|`sql:hide`|Прячет элемент или атрибут, заданные в схеме результирующего XML-документа.|[Скрытие элементов и атрибутов при помощи sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)|Не поддерживается|  
|`sql:identity`|Может быть задан для любого узла, сопоставляемого со столбцом типа IDENTITY. Значение, заданное для этой аннотации, определяет, каким образом будет изменяться соответствующий столбец типа IDENTITY в базе данных.|[Использование заметок sql:identity и sql:guid](using-the-sql-identity-and-sql-guid-annotations.md)|Не поддерживается|  
|`sql:inverse`|Указывает логике диаграмма обновления на обратную интерпретацию связи типа «родители-потомки», указанной с помощью ** \<SQL: relationship>**.|[Указание атрибута SQL: инверсии в SQL: relationship &#40;SQLXML 4,0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Не поддерживается|  
|`sql:is-constant`|Создает XML-элемент, который не сопоставлен ни с одной из таблиц. Этот элемент появляется в выходных данных запроса.|[Создание элементов констант с помощью SQL: является константой &#40;SQLXML 4,0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Аналогично|  
|`sql:key-fields`|Позволяет задавать определения столбцов, которые служат уникальными идентификаторами строк в таблице.|[Определение ключевых столбцов с помощью SQL: Key-Fields &#40;SQLXML 4,0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Аналогично|  
|`sql:limit-field`<br /><br /> `sql:limit-value`|Позволяет ограничить значения, возвращаемые на основе ограничения значений.|[Фильтрация значений с помощью SQL: limit-field и SQL: limit-value &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)|Аналогично|  
|`sql:mapped`|Позволяет исключать элементы схемы из результата.|[Исключение элементов схемы из результирующего XML-документа с помощью SQL: сопоставлено &#40;SQLXML 4,0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|`map-field`|  
|`sql:max-depth`|Позволяет указать глубину рекурсивных связей, заданных в схеме.|[Задание глубины рекурсивных связей с использованием sql:max-depth](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Не поддерживается|  
|`sql:overflow-field`|Определяет столбец базы данных, в котором содержатся данные переполнения.|[Получение невостребованных данных с помощью SQL: overflow-поля &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)|Аналогично|  
|`sql:prefix`|Создает допустимые XML ID, IDREF и IDREFS. Предваряет значения ID, IDREF и IDREFS строкой.|[Создание допустимых атрибутов типа ID, IDREF и IDREFS с помощью SQL: prefix &#40;SQLXML 4,0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Аналогично|  
|`sql:relationship`|Определяет связи между XML-элементами. Атрибуты `parent`, `child`, `parent-key` и `child-key` используются для задания связи.|[Указание связей с помощью SQL: relationship &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Имена атрибутов отличаются:<br /><br /> `key-relation`<br /><br /> `foreign-relation`<br /><br /> `key`<br /><br /> `foreign-key`|  
|`sql:use-cdata`|Позволяет задавать использование разделов CDATA для определенных элементов XML-документа.|[Создание разделов CDATA с помощью SQL: use-CDATA &#40;SQLXML 4,0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Аналогично|  
  
> [!NOTE]  
>  Собственный атрибут XSD `targetNamespace` заменяет заметку `target-namespace`, введенную в схеме сопоставления XDR в версии [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Указание целевого пространства имен с помощью атрибута targetNamespace &#40;SQLXML 4,0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
