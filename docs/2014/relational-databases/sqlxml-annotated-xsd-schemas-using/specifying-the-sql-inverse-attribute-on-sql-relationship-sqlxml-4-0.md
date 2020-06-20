---
title: 'Указание атрибута SQL: инверсия в SQL: Relationship (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b0781102371b98cced72a5a0edee70c9567c372
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003074"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Задание значения атрибута sql:inverse для sql:relationship (SQLXML 4.0)
  Атрибут `sql:inverse` полезен только при использовании схемы XSD диаграммой обновления или при массовой загрузке. `sql:inverse`Атрибут может быть указан в **\<sql:relationship>** элементе. В диаграммах обновления их логика задействует схему при определении таблиц и столбцов, обновляемых операцией диаграммы обновления. Связи типа «родители-потомки», заданные в схеме, определяют порядок, в котором записи будут изменены (вставлены или удалены).  
  
 Если в схеме XSD связь «родители-потомки» задана в обратном порядке отношения «первичный ключ — внешний ключ» между соответствующими столбцами базы данных, операции вставки или удаления диаграммы обновления завершатся ошибкой из-за нарушения первичного ключа или внешнего ключа. В таких случаях `sql:inverse` атрибут указывается ( `sql:inverse="true"` ) в **\<sql:relationship>** элементе, а логика диаграмма обновления обратно интерпретирует связь типа «родители-потомки», указанную в схеме.  
  
 Атрибут `sql:inverse` имеет логическое значение (0=false, 1=true). Допустимые значения: 0, 1, true и false.  
  
 Рабочий пример с помощью `sql:inverse` заметки см. в разделе [указание схемы сопоставления с заметками в диаграмма обновления](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также:  
 [Указание связей с помощью SQL: relationship &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
