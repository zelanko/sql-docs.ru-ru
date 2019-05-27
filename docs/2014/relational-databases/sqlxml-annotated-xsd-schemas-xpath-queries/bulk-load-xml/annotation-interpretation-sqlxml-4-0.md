---
title: Интерпретация заметки (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2db54a2bec501c3422cf19b1efab7cdb581420e0
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66013438"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Интерпретация заметки (SQLXML 4.0)
  В подразделах этого раздела приведено описание того, как осуществляется интерпретация заметок в схеме XSD при массовой загрузке XML. Поведение, описанное здесь, применимо также к заметкам в схеме XDR.  
  
> [!NOTE]  
>  Сведения в этих разделах описывают только заметки, используемые средствами массовой загрузки XML при обработке. Полный перечень заметок для схемы XSD, поддерживаемых в SQLXML 4.0, см. в разделе [использование заметок в схемах XSD &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Перечень поддерживаемых заметок для XDR-схемы, см. в разделе [аннотированные схемы XDR &#40;в SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [SQL: Relationship и правило упорядочения ключа &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Описывает способ интерпретации заметки `sql:relationship` при массовой загрузке XML.  
  
 [SQL: сопоставлены &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-mapped.md)  
 Описывает способ интерпретации заметки `sql:mapped` при массовой загрузке XML.  
  
 [SQL: Limit-поля и SQL: Limit-значение &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Описывает способ интерпретации заметок `sql:limit-field` и `sql:limit-value` при массовой загрузке XML.  
  
 [SQL: Overflow-поле &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-overflow-field.md)  
 Описывает способ интерпретации заметки `sql:overflow` при массовой загрузке XML.  
  
 [Другие аннотации &#40;SQLXML 4.0&#41;](annotation-interpretation-other-annotations.md)  
 Описывает способ интерпретации следующих заметок при массовой загрузке XML: `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.  
  
  
