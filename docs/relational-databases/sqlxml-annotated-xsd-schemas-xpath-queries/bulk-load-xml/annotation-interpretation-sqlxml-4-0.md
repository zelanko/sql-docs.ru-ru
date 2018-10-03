---
title: Интерпретация заметки (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5d4f968e0672d8072985479d39ed515e2207df12
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603542"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Интерпретация заметки (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В подразделах этого раздела приведено описание того, как осуществляется интерпретация заметок в схеме XSD при массовой загрузке XML. Поведение, описанное здесь, применимо также к заметкам в схеме XDR.  
  
> [!NOTE]  
>  Сведения в этих разделах описывают только заметки, используемые средствами массовой загрузки XML при обработке. Полный перечень заметок для схемы XSD, поддерживаемых в SQLXML 4.0, см. в разделе [использование заметок в схемах XSD &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Перечень поддерживаемых заметок для XDR-схемы, см. в разделе [аннотированные схемы XDR &#40;в SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [SQL: Relationship и правило упорядочения ключа &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Описывает способ **SQL: Relationship** Примечание интерпретируется в массовой загрузке XML.  
  
 [SQL: сопоставлены &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 Описывает способ **sql: сопоставлены** Примечание интерпретируется в массовой загрузке XML.  
  
 [SQL: Limit-поля и SQL: Limit-значение &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Описывает способ **SQL: Limit-поле** и **SQL: Limit-значение** интерпретации заметок Массовая загрузка XML.  
  
 [SQL: Overflow-поле &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Описывает способ **SQL: Overflow** Примечание интерпретируется в массовой загрузке XML.  
  
 [Другие аннотации &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 Описывает способ интерпретации следующих заметок при массовой загрузке XML: **SQL: ID-префикс**, **SQL: USE-cdata**, **заметки SQL: URL-кодирование**, **sql: — mapping-schema**, **SQL: Key-поля**.  
  
  
