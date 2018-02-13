---
title: "Использование заметок в схемах XSD (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c124bb466416e06768444ac7040c47a6267ae0d6
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Использование заметок в схемах XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
В [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 язык схем XSD поддерживает заметки аналогично заметкам, введенным в языке схем XDR. В XSD введены дополнительные заметки, не поддерживаемые в XDR.  
  
 Их можно использовать в схеме XSD для задания сопоставлений данных XML c реляционными данными. Сюда входит сопоставление элементов и атрибутов схемы XSD с таблицами (представлениями) и столбцами базы данных.  
  
 Если заметки не заданы, будет использоваться сопоставление по умолчанию. По умолчанию элемент XSD сложного типа сопоставляется имени таблицы или представления в заданной базе данных, а элемент или атрибут простого типа — одноименному столбцу.  
  
 Эти заметки можно также использовать для задания иерархических отношений в XML, представляя, таким образом, отношения в базе данных, поскольку схема XSD есть не что иное, как представление реляционных данных в виде XML.  
  
 Этот раздел представляет описания заметок, которые можно использовать со схемами XSD, и примеры их использования.  
  
> [!NOTE]  
>  Все примеры в этом разделе задают простые запросы XPath к схеме XSD с заметками, описанной в каждом из примеров. Предполагается, что читатель знаком с языком XPath.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Заметки XSD &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
 Перечисление заметок, которые можно использовать со схемами XSD, и эквивалентных им заметок для XDR.  
  
 [По умолчанию осуществляется сопоставление элементов и атрибутов таблиц и столбцов &#40; XSD SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Рассказ о сопоставлении по умолчанию и примеры задач, использующих такое сопоставление.  
  
 [Явное сопоставление элементов и атрибутов таблиц и столбцов &#40; XSD SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Содержит объяснение явного сопоставления с **SQL: Relation** и **SQL: field** заметки, а также примеры.  
  
 [Указание связей при помощи SQL: Relationship &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Описание и примеры **SQL: Relationship** заметки.  
  
 [Указание sql:inverse атрибут для SQL: Relationship &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Описывает **sql:inverse** заметки.  
  
 [Создание постоянных элементов при помощи sql: — константы &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Описание и примеры **sql: является константа** заметки.  
  
 [Исключение элементов схемы из результирующего XML-документа при помощи sql: сопоставленный &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Описание и примеры **sql: сопоставленный** заметки.  
  
 [Фильтрация значений при помощи SQL: Limit-поля и SQL: Limit-значение &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)  
 Описание и примеры **SQL: Limit-поле** и **SQL: Limit-значение** заметок.  
  
 [Определение ключевых столбцов с помощью SQL: Key-поля &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Описание и примеры **SQL: Key-поля** заметки.  
  
 [Указание целевого пространства имен с помощью атрибута targetNamespace &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Описание и примеры **targetNamespace** атрибута.  
  
 [Создание допустимый идентификатор, IDREF и IDREFS атрибуты типа с помощью SQL: prefix &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Описание и примеры **SQL: prefix** заметки.  
  
 [Приведение типов данных и заметка SQL: DataType &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Описание и примеры **SQL: DataType** заметки.  
  
 [Сопоставление типов данных XSD для типов данных XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)  
 Содержит таблицу сравнения типов данных XSD, XDR и XPath с перечислением соответствующих преобразований [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Создание разделов CDATA с использованием SQL: USE-cdata &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Описание и примеры **SQL: USE-данных** заметки.  
  
 [Запрос URL-ссылки на данные BLOB с помощью sql: encode &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Описание и примеры **sql: encode** заметки.  
  
 [Получение невостребованных данных при помощи SQL: Overflow-поле &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)  
 Описание и примеры **SQL: Overflow-поле** заметки.  
  
 [Скрытие элементов и атрибутов с помощью sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)  
 Описание и примеры **SQL: hide** заметки.  
  
 [Использование заметок sql:identity и sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)  
 Описание и примеры **: Identity** и **SQL: GUID** заметок.  
  
 [Задание глубины рекурсивных связей с использованием sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Описание и примеры **SQL: max-depth** заметки.  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности аннотированной схемы &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
