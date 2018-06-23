---
title: Использование заметок в схемах XSD (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 56db3f001d68bcaf65d71f793744896944318fc1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188191"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Использование заметок в схемах XSD (SQLXML 4.0)
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 язык схем XSD поддерживает заметки аналогично заметкам, введенным в языке схем XDR. В XSD введены дополнительные заметки, не поддерживаемые в XDR.  
  
 Их можно использовать в схеме XSD для задания сопоставлений данных XML c реляционными данными. Сюда входит сопоставление элементов и атрибутов схемы XSD с таблицами (представлениями) и столбцами базы данных.  
  
 Если заметки не заданы, будет использоваться сопоставление по умолчанию. По умолчанию элемент XSD сложного типа сопоставляется имени таблицы или представления в заданной базе данных, а элемент или атрибут простого типа — одноименному столбцу.  
  
 Эти заметки можно также использовать для задания иерархических отношений в XML, представляя, таким образом, отношения в базе данных, поскольку схема XSD есть не что иное, как представление реляционных данных в виде XML.  
  
 Этот раздел представляет описания заметок, которые можно использовать со схемами XSD, и примеры их использования.  
  
> [!NOTE]  
>  Все примеры в этом разделе задают простые запросы XPath к схеме XSD с заметками, описанной в каждом из примеров. Предполагается, что читатель знаком с языком XPath.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Заметки XSD &#40;SQLXML 4.0&#41;](xsd-annotations-sqlxml-4-0.md)  
 Перечисление заметок, которые можно использовать со схемами XSD, и эквивалентных им заметок для XDR.  
  
 [По умолчанию осуществляется сопоставление элементов и атрибутов с таблицами и столбцами XSD &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Рассказ о сопоставлении по умолчанию и примеры задач, использующих такое сопоставление.  
  
 [Явное сопоставление элементов и атрибутов с таблицами и столбцами XSD &#40;SQLXML 4.0&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Содержит объяснение явного сопоставления с заметками `sql:relation` и `sql:field`, а также примеры.  
  
 [Задание связей с помощью SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Содержит описание заметок `sql:relationship` и примеры.  
  
 [Указание sql:inverse атрибут для SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Описание заметки `sql:inverse`.  
  
 [Создание постоянных элементов при помощи sql: является константа &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Содержит описание заметок `sql:is-constant` и примеры.  
  
 [Исключение элементов схемы из результирующего XML-документа при помощи sql: сопоставленный &#40;SQLXML 4.0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Содержит описание заметок `sql:mapped` и примеры.  
  
 [Фильтрация значений при помощи SQL: Limit-поля и SQL: Limit-значение &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Содержит описание заметок `sql:limit-field` и `sql:limit-value`, а также примеры.  
  
 [Определение ключевых столбцов с помощью SQL: Key-поля &#40;SQLXML 4.0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Содержит описание заметок `sql:key-fields` и примеры.  
  
 [Указание целевого пространства имен с помощью атрибута targetNamespace &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Описание и примеры **targetNamespace** атрибута.  
  
 [Создание допустимый идентификатор, IDREF и IDREFS атрибуты типа с помощью SQL: prefix &#40;SQLXML 4.0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Содержит описание заметок `sql:prefix` и примеры.  
  
 [Приведение типов данных и заметка SQL: DataType &#40;SQLXML 4.0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Содержит описание заметок `sql:datatype` и примеры.  
  
 [Сопоставление типов данных XSD в типы данных XPath &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 Содержит таблицу сравнения типов данных XSD, XDR и XPath с перечислением соответствующих преобразований [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Создание разделов CDATA с использованием SQL: USE-cdata &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Содержит описание заметок `sql:use-data` и примеры.  
  
 [Запрос URL-ссылки на данные BLOB с помощью sql: encode &#40;SQLXML 4.0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Содержит описание заметок `sql:encode` и примеры.  
  
 [Получение невостребованных данных при помощи SQL: Overflow-поле &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Содержит описание заметок `sql:overflow-field` и примеры.  
  
 [Скрытие элементов и атрибутов с помощью sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)  
 Содержит описание заметок `sql:hide` и примеры.  
  
 [Использование заметок sql:identity и sql:guid](using-the-sql-identity-and-sql-guid-annotations.md)  
 Содержит описание заметок `sql:identity` и `sql:guid`, а также примеры.  
  
 [Задание глубины рекурсивных связей с использованием sql:max-depth](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Содержит описание заметок `sql:max-depth` и примеры.  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности схемы с заметками &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  