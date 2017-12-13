---
title: "Набор строк MDSCHEMA_MEMBERS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_MEMBERS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bff8fc8c121f88dbc8bf7cbdc0b2ce1705934702
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mdschemamembers-rowset"></a>Набор строк MDSCHEMA_MEMBERS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Описывает элементы в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **MDSCHEMA_MEMBERS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Имя базы данных, которой принадлежит элемент.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Имя схемы, которой принадлежит элемент.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Имя куба, которому принадлежит элемент.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя измерения, которому принадлежит элемент.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя иерархии, которой принадлежит элемент.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя уровня, которому принадлежит элемент.|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**||Расстояние от элемента до корня иерархии. Корневой уровень имеет нулевое значение (0).|  
|**MEMBER_ORDINAL**|**DBTYPE_UI4**||(Устарело) Всегда возвращает **0**.|  
|**MEMBER_NAME**|**DBTYPE_WSTR**||Имя элемента.|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя элемента.|  
|**MEMBER_TYPE**|**DBTYPE_I4**||Тип элемента:<br /><br /> **MDMEMBER_TYPE_UNKNOWN** (**0**)<br /><br /> **MDMEMBER_TYPE_REGULAR** (**1**)<br /><br /> **MDMEMBER_TYPE_ALL** (**2**)<br /><br /> **MDMEMBER_TYPE_MEASURE** (**3**)<br /><br /> **MDMEMBER_TYPE_FORMULA** (**4**)<br /><br /> <br /><br /> Обратите внимание, что <br />                    **MDMEMBER_TYPE_FORMULA**имеет приоритет над **MDMEMBER_TYPE_MEASURE**. Например, если имеется формула (вычисляемый) элемент в измерении мер, это отображается как **MDMEMBER_TYPE_FORMULA**.|  
|**MEMBER_GUID**|**DBTYPE_GUID**||Идентификатор GUID элемента. **Значение NULL** Если идентификатор GUID не существует.|  
|**MEMBER_CAPTION**|**DBTYPE_WSTR**||Метка или заголовок, связанный с элементом. В основном используется в целях отображения. Если заголовок не существует, **MEMBER_NAME** возвращается.|  
|**CHILDREN_CARDINALITY**|**DBTYPE_UI4**||Количество потомков элемента. Значение этого свойства может представлять собой оценку, поэтому потребителям не следует рассчитывать на то, что оно точно показывает количество. Поставщики должны возвращать возможное наивернейшее приблизительное значение.|  
|**PARENT_LEVEL**|**DBTYPE_UI4**||Расстояние от родительского элемента данного элемента до корневого уровня иерархии. Корневой уровень имеет нулевое значение (0).|  
|**PARENT_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя родителя элемента. Для любых элементов на корневом уровне возвращается значение**NULL** .|  
|**PARENT_COUNT**|**DBTYPE_UI4**||Количество родительских элементов данного элемента.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Этот столбец всегда возвращает **NULL** значение.<br /><br /> Этот столбец предусмотрен для обеспечения обратной совместимости.|  
|**ВЫРАЖЕНИЕ**|**DBTYPE_WSTR**||Выражение для вычисления, если элемент имеет тип **MDMEMBER_TYPE_FORMULA**.|  
|**MEMBER_KEY**|**DBTYPE_WSTR**||Значение ключевого столбца элемента. Возвращает **NULL** Если элемент имеет составной ключ.|  
|**IS_PLACEHOLDERMEMBER**|**DBTYPE_BOOL**||Логическое значение, которое указывает, является ли данный элемент элементом заполнителя для пустой позиции в иерархии измерения.<br /><br /> Он допустим только тогда, когда **MDX Compatibility** свойство значение 2.|  
|**IS_DATAMEMBER**|**DBTYPE_BOOL**||Логическое значение, указывающее, является ли элемент элементом данных.<br /><br /> Возвращает True, если элемент является элементом данных.|  
|**ОБЛАСТЬ ДЕЙСТВИЯ**|**DBTYPE_I4**||Область элемента. Элемент может быть элементом, вычисляемым в сеансе, или элементом, вычисляемым глобально. Возвращает столбец **NULL** для невычисляемых элементов. Этот столбец может иметь одно из следующих значений.<br /><br /> MDMEMBER_SCOPE_GLOBAL=1<br /><br /> MDMEMBER_SCOPE_SESSION=2|  
|**Ноль или более дополнительных столбцов**|**DBTYPE_UI2**||Не происходит возврат каких-либо свойств, если элементы могут быть возвращены с нескольких уровней. Например, если оператор дерева представляет собой **РОДИТЕЛЬСКОГО** и **SELF** для иерархии родители-потомки, возвращаются никаких свойств элемента.<br /><br /> Это относится к неоднородным иерархиям, из которых операторы дерева могут возвращать элементы разных уровней (например, если предыдущий уровень содержит пропуски, но требуется получить родительский элемент для какого-то элемента).|  
  
 Набор строк отсортирован по **CATALOG_NAME**, **имя_схемы**, **CUBE_NAME**, **DIMENSION_UNIQUE_NAME**, **HIERARCHY_ UNIQUE_NAME**, **LEVEL_UNIQUE_NAME**, **LEVEL_NUMBER**, **MEMBER_ORDINAL**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **MDSCHEMA_MEMBERS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**LEVEL_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**LEVEL_NUMBER**|**DBTYPE_UI4**|Необязательно.|  
|**MEMBER_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEMBER_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**MEMBER_CAPTION**|**DBTYPE_WSTR**|Необязательно.|  
|**MEMBER_TYPE**|**DBTYPE_I4**|Необязательно.|  
|**TREE_OP**|**DBTYPE_I4**|Применяется только к единственному элементу (необязательно):<br /><br /> **MDTREEOP_ANCESTORS** (**0x20**) возвращает всех предков.<br /><br /> **MDTREEOP_CHILDREN** (**0x01**) возвращает только непосредственные дочерние элементы.<br /><br /> **MDTREEOP_SIBLINGS** (**0x02**) возвращает элементы на том же уровне.<br /><br /> **MDTREEOP_PARENT** (**0x04**) возвращает только непосредственного родителя.<br /><br /> **MDTREEOP_SELF** (**0x08**) возвращает себя в списке возвращенных строк.<br /><br /> **MDTREEOP_DESCENDANTS** (**0x10**) возвращает всех потомков.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Необязательно) Ограничение по умолчанию имеет значение 1. Битовая карта с одним из следующих допустимых значений:<br /><br /> 1 CUBE<br /><br /> 2 DIMENSION|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы OLE DB для OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
