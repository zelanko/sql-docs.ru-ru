---
title: "Интерпретация заметки (SQLXML 4.0) | Документы Microsoft"
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
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f2d066414f6835f0803d6530e0ea1fa187c04ff
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="annotation-interpretation-sqlxml-40"></a>Интерпретация заметки (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
В подразделах этого раздела приведено описание того, как осуществляется интерпретация заметок в схеме XSD при массовой загрузке XML. Поведение, описанное здесь, применимо также к заметкам в схеме XDR.  
  
> [!NOTE]  
>  Сведения в этих разделах описывают только заметки, используемые средствами массовой загрузки XML при обработке. Полный список заметок для схемы XSD, поддерживаемых в SQLXML 4.0 см. в разделе [использование заметок в схемах XSD &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Перечень поддерживаемых заметок для схем XDR см. в разделе [аннотированные схемы XDR &#40; устарел в SQLXML 4.0 &#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [&#40; SQL: Relationship и правило упорядочения ключа SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Описывает способ **SQL: Relationship** Примечание интерпретируется в массовой загрузке XML.  
  
 [SQL: сопоставленный &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 Описывает способ **sql: сопоставленный** Примечание интерпретируется в массовой загрузке XML.  
  
 [SQL: Limit-поля и SQL: Limit-значение &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Описывает способ **SQL: Limit-поле** и **SQL: Limit-значение** интерпретации заметок массовой загрузке XML.  
  
 [SQL: Overflow-поле &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Описывает способ **SQL: Overflow** Примечание интерпретируется в массовой загрузке XML.  
  
 [Другие заметки &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 Описывает способ интерпретации следующих заметок массовой загрузке XML: **SQL: ID-префикс**, **SQL: USE-cdata**, **заметки SQL: URL-encode**, **sql: — mapping-schema**, **SQL: Key-поля**.  
  
  
