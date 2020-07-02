---
title: Интерпретация аннотации (SQLXML)
description: Узнайте, как с помощью групповой нагрузки XML в SQLXML 4,0 интерпретирует заметки в схемах XSD и XDR.
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
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 41cb1a0e65b7e453f408a43b71b1cad831b0cba4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790889"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Интерпретация заметки (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  В подразделах этого раздела приведено описание того, как осуществляется интерпретация заметок в схеме XSD при массовой загрузке XML. Поведение, описанное здесь, применимо также к заметкам в схеме XDR.  
  
> [!NOTE]  
>  Сведения в этих разделах описывают только заметки, используемые средствами массовой загрузки XML при обработке. Полный список заметок для схемы XSD, поддерживаемых SQLXML 4,0, см. [в разделе Использование заметок в схемах xsd &#40;sqlxml 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Список поддерживаемых заметок для схем XDR см. [в разделе схемы XDR с Заметками &#40;нерекомендуемые в SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [SQL: отношение и правило упорядочивания ключей &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Описывает, как заметка **SQL: relationship** интерпретируется при выполнении групповой загрузки XML.  
  
 [SQL: сопоставленная &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 Описывает, как заметка **SQL: сопоставленная** Аннотация интерпретируется при выполнении групповой загрузки XML.  
  
 [SQL: limit-field и SQL: limit-value &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Описывает, как заметки **SQL: limit-field** и **SQL: limit-value** обрабатываются при выполнении групповой загрузки XML.  
  
 [SQL: overflow — поле &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Описывает, как интерпретируется Аннотация **SQL: overflow** при выполнении групповой загрузки XML.  
  
 [Другие заметки &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 Описывает интерпретацию следующих аннотаций при выполнении групповой загрузки XML: **SQL: id-prefix**, **SQL: use-CDATA**, **SQL: URL-encoded**, **SQL:-Mapping-Schema**, **SQL: Key-Fields**.  
  
  
