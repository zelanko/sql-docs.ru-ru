---
title: 'Указание значения атрибута SQL: inverse для SQL: Relationship (SQLXML 4.0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5bb1d16ef1caf6622a2da1dd1c2c9674cf2b9d0c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164584"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Задание значения атрибута sql:inverse для sql:relationship (SQLXML 4.0)
  Атрибут `sql:inverse` полезен только при использовании схемы XSD диаграммой обновления или при массовой загрузке. `sql:inverse` Атрибут может быть указан в  **\<SQL: Relationship >** элемент. В диаграммах обновления их логика задействует схему при определении таблиц и столбцов, обновляемых операцией диаграммы обновления. Связи типа «родители-потомки», заданные в схеме, определяют порядок, в котором записи будут изменены (вставлены или удалены).  
  
 Если в схеме XSD связь «родители-потомки» задана в обратном порядке отношения «первичный ключ — внешний ключ» между соответствующими столбцами базы данных, операции вставки или удаления диаграммы обновления завершатся ошибкой из-за нарушения первичного ключа или внешнего ключа. В таких случаях `sql:inverse` указан атрибут (`sql:inverse="true"`) в  **\<SQL: Relationship >** элемента и инверсии логика диаграммы обновления его интерпретации отношения родитель потомок указанного в схеме.  
  
 Атрибут `sql:inverse` имеет логическое значение (0=false, 1=true). Допустимые значения: 0, 1, true и false.  
  
 Для рабочий образец, использующий `sql:inverse` заметки, см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также  
 [Указание связей с помощью SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
