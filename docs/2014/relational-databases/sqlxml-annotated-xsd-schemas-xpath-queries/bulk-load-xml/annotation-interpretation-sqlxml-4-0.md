---
title: Интерпретация аннотации (SQLXML 4,0) | Документация Майкрософт
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 80b472ee00aba60e2bc01883b79b570dbed07b4f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703396"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Интерпретация заметки (SQLXML 4.0)
  В подразделах этого раздела приведено описание того, как осуществляется интерпретация заметок в схеме XSD при массовой загрузке XML. Поведение, описанное здесь, применимо также к заметкам в схеме XDR.  
  
> [!NOTE]  
>  Сведения в этих разделах описывают только заметки, используемые средствами массовой загрузки XML при обработке. Полный список заметок для схемы XSD, поддерживаемых SQLXML 4,0, см. [в разделе Использование заметок в схемах xsd &#40;sqlxml 4,0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Список поддерживаемых заметок для схем XDR см. [в разделе схемы XDR с Заметками &#40;нерекомендуемые в SQLXML 4,0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [SQL: отношение и правило упорядочивания ключей &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Описывает способ интерпретации заметки `sql:relationship` при массовой загрузке XML.  
  
 [SQL: сопоставленная &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-mapped.md)  
 Описывает способ интерпретации заметки `sql:mapped` при массовой загрузке XML.  
  
 [SQL: limit-field и SQL: limit-value &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Описывает способ интерпретации заметок `sql:limit-field` и `sql:limit-value` при массовой загрузке XML.  
  
 [SQL: overflow — поле &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-overflow-field.md)  
 Описывает способ интерпретации заметки `sql:overflow` при массовой загрузке XML.  
  
 [Другие заметки &#40;SQLXML 4,0&#41;](annotation-interpretation-other-annotations.md)  
 Описывает интерпретацию следующих аннотаций при выполнении групповой загрузки XML: `sql:id-prefix` , `sql:use-cdata` , `sql:url-encode` , `sql:is-mapping-schema` , `sql:key-fields` .  
  
  
