---
title: Набор строк DMSCHEMA_MINING_MODEL_CONTENT | Документация Майкрософт
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
- DMSCHEMA_MINING_MODEL_CONTENT
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT rowset
ms.assetid: 1e85d9e7-3b74-42ac-b94e-f52f76d8a25d
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 76724967936008e52cb43f7af02bbb7a833475d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165455"
---
# <a name="dmschemaminingmodelcontent-rowset"></a>Набор строк DMSCHEMA_MINING_MODEL_CONTENT
  Разрешает клиентскому приложению просматривать содержимое модели интеллектуального анализа данных. Клиентские приложения для перемещений по содержимому модели интеллектуального анализа данных могут применять специальные ограничения операций дерева, описанные в конце этого раздела.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DMSCHEMA_MINING_MODEL_CONTENT` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Имя каталога. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] заполняет этот столбец имя базы данных, членом которой является модель.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Неполное имя схемы. Этот столбец не поддерживается службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и всегда содержит значение `VT_NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Имя модели, с которой связано содержимое, описанное в этой строке.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Имена атрибутов, соответствующих этому узлу.|  
|`NODE_NAME`|`DBTYPE_WSTR`||Имя узла. В текущей версии этот столбец содержит то же значение, что и `NODE_UNIQUE_NAME`, но такое соответствие может измениться в следующих версиях.|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя узла.|  
|`NODE_TYPE`|`DBTYPE_I4`||Тип узла. Выдает одно из следующих значений (этот список могут продолжить алгоритмами интеллектуального анализа данных сторонней разработки).<br /><br /> -   `DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT` (`2`)<br />-   `DM_NODE_TYPE_TREE_INTERIOR` (`3`)<br />-   `DM_NODE_TYPE_TREE_DISTRIBUTION` (`4`)<br />-   `DM_NODE_TYPE_CLUSTER` (`5`)<br />-   `DM_NODE_TYPE_UNKNOWN` (`6`)<br />-   `DM_NODE_TYPE_ITEMSET` (`7`)<br />-   `DM_NODE_TYPE_ASSOCIATION_RULE` (`8`)<br />-   `DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE` (`9`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE` (`10`)<br />-   `DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE` (`11`)<br />-   `DM_NODE_TYPE_SEQUENCE` (`13`)<br />-   `DM_NODE_TYPE_TRANSITION` (`14`)<br />-   `DM_NODE_TYPE_TIME_SERIES` (`15`)<br />-   `DM_NODE_TYPE_TS_TREE` (`16`)<br />-   `DM_NODE_TYPE_NN_SUBNETWORK` (`17`) Нейронная сеть, подсеть<br />-   `DM_NODE_TYPE_NN_INPUT_LAYER` (`18`) Нейронная сеть, входной уровень (родитель входных узлов)<br />-   **DM_NODE_TYPE_NN_HIDDEN_LAYER** (`19`) Нейронная сеть, скрытый уровень (родитель скрытых узлов)<br />-   `DM_NODE_TYPE_NN_OUTPUT_LAYER` (`20`) Нейронная сеть, выходной уровень (родитель выходных узлов)<br />-   `DM_NODE_TYPE_NN_INPUT_NODE` (`21`) Нейронная сеть, входной узел<br />-   `DM_NODE_TYPE_NN_HIDDEN_NODE` (`22`) Нейронная сеть, скрытый узел<br />-   `DM_NODE_TYPE_NN_OUTPUT_NODE` (`23`) Нейронная сеть, выходной узел<br />-   `DM_NODE_TYPE_NN_MARGINAL_STAT_NODE` (`24`) Нейронная сеть, граничной статистики<br />-   **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (`25`)<br />-   `DM_NODE_TYPE_NB_MARGINAL_STAT_NODE` (`26`) Нейронная сеть, граничной статистики|  
|`NODE_GUID`|`DBTYPE_GUID`||Идентификатор GUID узла. Этот столбец не поддерживается службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и всегда содержит значение `NULL`.|  
|`NODE_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с узлом. Этой свойство используется главным образом для отображения.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Оценка количества дочерних узлов, которые имеет данный узел.|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Уникальное имя родителя узла. Для любых узлов на корневом уровне возвращается значение `NULL`.|  
|`NODE_DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание узла.|  
|`NODE_RULE`|`DBTYPE_WSTR`||XML-описание правила, внедренного в узел.|  
|`MARGINAL_RULE`|`DBTYPE_WSTR`||XML-описание правила, перемещенного в узел из родительского узла.|  
|`NODE_PROBABILITY`|`DBTYPE_R8`||Вероятность, связанная с этим узлом.|  
|`MARGINAL_PROBABILITY`|`DBTYPE_R8`||Вероятность доступа к узлу от родительского узла.|  
|`NODE_DISTRIBUTION`|`DBTYPE_HCHAPTER`||Таблица, содержащая гистограмму вероятности узла.|  
|`NODE_SUPPORT`|`DBTYPE_R8`||Число вариантов, поддерживаемое этим узлом.|  
|`MSOLAP_MODEL_COLUMN`|`DBTYPE_WSTR`||Имя столбца из определения модели, к которому имеет отношение этот узел.|  
|`MSOLAP_NODE_SCORE`|`DBTYPE_R8`||Оценка, вычисленная для этого узла.|  
|`MSOLAP_NODE_SHORT_CAPTION`|`DBTYPE_WSTR`||Краткий заголовок для узла, который можно использовать для наглядности и понятности.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DMSCHEMA_MINING_MODEL_CONTENT` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`NODE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`NODE_UNIQUE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`NODE_TYPE`|`DBTYPE_I4`|Необязательный параметр.|  
|`NODE_GUID`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`NODE_CAPTION`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`TREE_OPERATION`|`DBTYPE_UI4`|Необязательный параметр. Ниже приведены дополнительные примечания.|  
  
 Ограничение `TREE_OPERATION` не относится к какому-либо конкретному столбцу в наборе строк `DMSCHEMA_MINING_MODEL_CONTENT`. Оно указывает оператор дерева. Для получения требуемого набора элементов пользователь может указать ограничение `NODE_UNIQUE_NAME` и оператор дерева (`ANCESTORS`, `CHILDREN`, `SIBLINGS`, `PARENT`, `DESCENDANTS`, `SELF`). Оператор `SELF` включает строку для самого узла в список возвращенных строк. В приведенной ниже таблице описаны константы, составляющие определение битовой карты для ограничения `TREE_OPERATION`. Их можно сочетать с помощью логического оператора `OR`.  
  
|Константа|Значение|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|`0x00000020`|  
|**DMTREEOP_CHILDREN**|`0x00000001`|  
|**DMTREEOP_SIBLINGS**|`0x00000002`|  
|**DMTREEOP_PARENT**|`0x00000004`|  
|**DMTREEOP_SELF**|`0x00000008`|  
|**DMTREEOP_DESCENDANTS**|`0x00000010`|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы интеллектуального анализа данных](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
