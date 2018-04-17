---
title: 'Указание sql:inverse атрибут для SQL: Relationship (SQLXML 4.0) | Документы Microsoft'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c71271c88cdae1d62e429232039d64d77eedfb81
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Задание значения атрибута sql:inverse для sql:relationship (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **Sql:inverse** атрибут полезен, только если XSD-схемы используемого массовой загрузке или диаграммы обновления. **Sql:inverse** может быть задан атрибут  **\<SQL: Relationship >** элемента. В диаграммах обновления их логика задействует схему при определении таблиц и столбцов, обновляемых операцией диаграммы обновления. Связи типа «родители-потомки», заданные в схеме, определяют порядок, в котором записи будут изменены (вставлены или удалены).  
  
 Если в схеме XSD связь «родители-потомки» задана в обратном порядке отношения «первичный ключ — внешний ключ» между соответствующими столбцами базы данных, операции вставки или удаления диаграммы обновления завершатся ошибкой из-за нарушения первичного ключа или внешнего ключа. В таких случаях **sql:inverse** указан атрибут (**sql:inverse = «true»**) в  **\<SQL: Relationship >** элемент и логике диаграммы обновления инверсиями интерпретацию связи "родитель потомок" указан в схеме.  
  
 **Sql:inverse** атрибут принимает логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false.  
  
 Для рабочий образец, использующий **sql:inverse** заметки, в разделе [указание схемы с заметками сопоставления в диаграмме обновления](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также  
 [Задание связей с помощью SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
