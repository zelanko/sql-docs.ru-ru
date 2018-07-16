---
title: Набор строк MDSCHEMA_MEMBERS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_MEMBERS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d36a065ea73f249ce5c4d9dc37cc047ac864cb84
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280020"
---
# <a name="mdschemamembers-rowset"></a>Набор строк MDSCHEMA_MEMBERS
  Описывает элементы в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_MEMBERS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных, которой принадлежит элемент.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Имя схемы, которой принадлежит элемент.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба, которому принадлежит элемент.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя измерения, которому принадлежит элемент.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя иерархии, которой принадлежит элемент.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя уровня, которому принадлежит элемент.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Расстояние от элемента до корня иерархии. Корневой уровень имеет нулевое значение (0).|  
|`MEMBER_ORDINAL`|`DBTYPE_UI4`||Всегда возвращает `0` (является устаревшим).|  
|`MEMBER_NAME`|`DBTYPE_WSTR`||Имя элемента.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя элемента.|  
|`MEMBER_TYPE`|`DBTYPE_I4`||Тип элемента:<br /><br /> -   `MDMEMBER_TYPE_REGULAR` (`1`)<br />-   `MDMEMBER_TYPE_ALL` (`2`)<br />-   `MDMEMBER_TYPE_MEASURE` (`3`)<br />-   `MDMEMBER_TYPE_FORMULA` (`4`)<br />-   `MDMEMBER_TYPE_UNKNOWN` (`0`)<br />-   `MDMEMBER_TYPE_FORMULA` имеет приоритет над `MDMEMBER_TYPE_MEASURE`. Например, если в измерении мер имеется (вычисляемый) элемент формулы, то он приводится как `MDMEMBER_TYPE_FORMULA`.|  
|`MEMBER_GUID`|`DBTYPE_GUID`||Идентификатор GUID элемента. Значение `NULL`, если идентификатор GUID не существует.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с элементом. В основном используется в целях отображения. Если заголовок не существует, возвращается `MEMBER_NAME`.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Количество потомков элемента. Значение этого свойства может представлять собой оценку, поэтому потребителям не следует рассчитывать на то, что оно точно показывает количество. Поставщики должны возвращать возможное наивернейшее приблизительное значение.|  
|`PARENT_LEVEL`|`DBTYPE_UI4`||Расстояние от родительского элемента данного элемента до корневого уровня иерархии. Корневой уровень имеет нулевое значение (0).|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя родителя элемента. Для любых элементов на корневом уровне возвращается значение `NULL`.|  
|`PARENT_COUNT`|`DBTYPE_UI4`||Количество родительских элементов данного элемента.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Этот столбец всегда возвращает значение `NULL`.<br /><br /> Этот столбец предусмотрен для обеспечения обратной совместимости.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Выражение для вычислений, если элемент имеет тип `MDMEMBER_TYPE_FORMULA`.|  
|`MEMBER_KEY`|`DBTYPE_WSTR`||Значение ключевого столбца элемента. Возвращает значение `NULL`, если элемент имеет составной ключ.|  
|`IS_PLACEHOLDERMEMBER`|`DBTYPE_BOOL`||Логическое значение, которое указывает, является ли данный элемент элементом заполнителя для пустой позиции в иерархии измерения.<br /><br /> Допустимо, только если свойство `MDX Compatibility` было установлено равным 2.|  
|`IS_DATAMEMBER`|`DBTYPE_BOOL`||Логическое значение, указывающее, является ли элемент элементом данных.<br /><br /> Возвращает True, если элемент является элементом данных.|  
|`SCOPE`|`DBTYPE_I4`||Область элемента. Элемент может быть элементом, вычисляемым в сеансе, или элементом, вычисляемым глобально. Столбец возвращает значение `NULL` для невычисляемых элементов.<br /><br /> Этот столбец может иметь одно из следующих значений.<br /><br /> -MDMEMBER_SCOPE_GLOBAL = 1<br />-MDMEMBER_SCOPE_SESSION = 2|  
|`Zero or more additional columns`|`DBTYPE_UI2`||Не происходит возврат каких-либо свойств, если элементы могут быть возвращены с нескольких уровней. Например, если для неродительской дочерней иерархии оператор дерева представляет собой `PARENT` и `SELF`, то не происходит возврата никаких свойств элемента.<br /><br /> Это относится к неоднородным иерархиям, из которых операторы дерева могут возвращать элементы разных уровней (например, если предыдущий уровень содержит пропуски, но требуется получить родительский элемент для какого-то элемента).|  
  
 Набор строк отсортирован по `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_UNIQUE_NAME`, `LEVEL_NUMBER`, `MEMBER_ORDINAL`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_MEMBERS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`|Необязательный параметр.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MEMBER_TYPE`|`DBTYPE_I4`|Необязательный параметр.|  
|`TREE_OP`|`DBTYPE_I4`|Применяется только к единственному элементу (необязательно):<br /><br /> -   `MDTREEOP_ANCESTORS` (`0x20`) возвращает всех предков.<br />-   `MDTREEOP_CHILDREN` (`0x01`) возвращает только непосредственные дочерние элементы.<br />-   `MDTREEOP_SIBLINGS` (`0x02`) возвращает элементы на одном уровне.<br />-   `MDTREEOP_PARENT` (`0x04`) возвращает только непосредственного родителя.<br />-   `MDTREEOP_SELF` (`0x08`) возвращает себя в списке возвращенных строк.<br />-   `MDTREEOP_DESCENDANTS` (`0x10`) возвращает всех потомков.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />— ИЗМЕРЕНИЯ 2<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
