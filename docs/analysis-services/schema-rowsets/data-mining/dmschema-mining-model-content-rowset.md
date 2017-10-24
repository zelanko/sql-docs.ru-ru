---
title: "Набор строк DMSCHEMA_MINING_MODEL_CONTENT | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_MODEL_CONTENT
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT rowset
ms.assetid: 1e85d9e7-3b74-42ac-b94e-f52f76d8a25d
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7d48b47cc0ded0541380a4a9997b1cab13bd21a0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingmodelcontent-rowset"></a>Набор строк DMSCHEMA_MINING_MODEL_CONTENT
  Разрешает клиентскому приложению просматривать содержимое модели интеллектуального анализа данных. Клиентские приложения для перемещений по содержимому модели интеллектуального анализа данных могут применять специальные ограничения операций дерева, описанные в конце этого раздела.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DMSCHEMA_MINING_MODEL_CONTENT** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Имя каталога. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] помещает в него имя базы данных, членом которой является модель.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Неполное имя схемы. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **VT_NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Имя модели, с которой связано содержимое, описанное в этой строке.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Имена атрибутов, соответствующих этому узлу.|  
|**NODE_NAME**|**DBTYPE_WSTR**||Тип узла. В настоящее время этот столбец содержит то же значение, что **NODE_UNIQUE_NAME**, хотя это может измениться в будущих выпусках.|  
|**NODE_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя узла.|  
|**NODE_TYPE**|**DBTYPE_I4**||Тип узла. Выдает одно из следующих значений (этот список могут продолжить алгоритмами интеллектуального анализа данных сторонней разработки).<br /><br /> **DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT** (**2**)<br /><br /> **DM_NODE_TYPE_TREE_INTERIOR** (**3**)<br /><br /> **DM_NODE_TYPE_TREE_DISTRIBUTION** (**4**)<br /><br /> **DM_NODE_TYPE_CLUSTER** (**5**)<br /><br /> **DM_NODE_TYPE_UNKNOWN** (**6**)<br /><br /> **DM_NODE_TYPE_ITEMSET** (**7**)<br /><br /> **DM_NODE_TYPE_ASSOCIATION_RULE** (**8**)<br /><br /> **DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE** (**9**)<br /><br /> **DM_NODE_TYPE_NB_INPUT_ATTRIBUTE** (**10**)<br /><br /> **DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE** (**11**)<br /><br /> **DM_NODE_TYPE_SEQUENCE** (**13**)<br /><br /> **DM_NODE_TYPE_TRANSITION** (**14**)<br /><br /> **DM_NODE_TYPE_TIME_SERIES** (**15**)<br /><br /> **DM_NODE_TYPE_TS_TREE** (**16**)<br /><br /> **DM_NODE_TYPE_NN_SUBNETWORK** (**17**) Нейронная сеть, подсеть<br /><br /> **DM_NODE_TYPE_NN_INPUT_LAYER** (**18**) Нейронная сеть, входной уровень (родитель входных узлов)<br /><br /> **DM_NODE_TYPE_NN_HIDDEN_LAYER** (**19**) Нейронная сеть, скрытый уровень (родитель скрытых узлов)<br /><br /> **DM_NODE_TYPE_NN_OUTPUT_LAYER** (**20**) Нейронная сеть, выходной уровень (родитель выходных узлов)<br /><br /> **DM_NODE_TYPE_NN_INPUT_NODE** (**21**) Нейронная сеть, входной узел<br /><br /> **DM_NODE_TYPE_NN_HIDDEN_NODE** (**22**) Нейронная сеть, скрытый узел<br /><br /> **DM_NODE_TYPE_NN_OUTPUT_NODE** (**23**) Нейронная сеть, выходной узел<br /><br /> **DM_NODE_TYPE_NN_MARGINAL_STAT_NODE** (**24**) Нейронная сеть, узел граничной статистики<br /><br /> **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (**25**)<br /><br /> **DM_NODE_TYPE_NB_MARGINAL_STAT_NODE** (**26**) Нейронная сеть, узел граничной статистики|  
|**NODE_GUID**|**DBTYPE_GUID**||Идентификатор GUID узла. Этот столбец не поддерживается [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; он всегда содержит **NULL**.|  
|**NODE_CAPTION**|**DBTYPE_WSTR**||Метка или заголовок, связанный с узлом. Этой свойство используется главным образом для отображения.|  
|**CHILDREN_CARDINALITY**|**DBTYPE_UI4**||Оценка количества дочерних узлов, которые имеет данный узел.|  
|**PARENT_UNIQUE_NAME**|**DBTYPE_WSTR**||Уникальное имя родителя узла. **Значение NULL** возвращается для любых узлов на корневом уровне.|  
|**NODE_DESCRIPTION**|**DBTYPE_WSTR**||Понятное описание узла.|  
|**NODE_RULE**|**DBTYPE_WSTR**||XML-описание правила, внедренного в узел.|  
|**MARGINAL_RULE**|**DBTYPE_WSTR**||XML-описание правила, перемещенного в узел из родительского узла.|  
|**С NODE_PROBABILITY**|**DBTYPE_R8**||Вероятность, связанная с этим узлом.|  
|**MARGINAL_PROBABILITY**|**DBTYPE_R8**||Вероятность доступа к узлу от родительского узла.|  
|**NODE_DISTRIBUTION**|**DBTYPE_HCHAPTER**||Таблица, содержащая гистограмму вероятности узла.|  
|**NODE_SUPPORT**|**DBTYPE_R8**||Число вариантов, поддерживаемое этим узлом.|  
|**MSOLAP_MODEL_COLUMN**|**DBTYPE_WSTR**||Имя столбца из определения модели, к которому имеет отношение этот узел.|  
|**MSOLAP_NODE_SCORE**|**DBTYPE_R8**||Оценка, вычисленная для этого узла.|  
|**СТОЛБЕЦ MSOLAP_NODE_SHORT_CAPTION**|**DBTYPE_WSTR**||Краткий заголовок для узла, который можно использовать для наглядности и понятности.|  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DMSCHEMA_MINING_MODEL_CONTENT** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Необязательно.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**NODE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**NODE_UNIQUE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
|**NODE_TYPE**|**DBTYPE_I4**|Необязательно.|  
|**NODE_GUID**|**DBTYPE_WSTR**|Необязательно.|  
|**NODE_CAPTION**|**DBTYPE_WSTR**|Необязательно.|  
|**TREE_OPERATION**|**DBTYPE_UI4**|Необязательно. Ниже приведены дополнительные примечания.|  
  
 Ограничения, **TREE_OPERATION**, не находится на любого столбца из **DMSCHEMA_MINING_MODEL_CONTENT** строк; оно указывает оператор дерева. Потребитель может указать **NODE_UNIQUE_NAME** ограниченного использования программ и оператор дерева (**ПРЕДКОВ**, **ДОЧЕРНИХ**, **одноуровневых ЭЛЕМЕНТОВ**,  **Родительский**, **потомков**, **SELF**) для получения требуемого набора элементов. **SELF** оператор включает строку для самого узла в списке возвращенных строк. В следующей таблице описаны константы, составляющие определение битовой карты для **TREE_OPERATION** ограниченного использования программ. Они могут быть объединены с помощью логического **или** оператор.  
  
|Константа|Значение|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|**0x00000020**|  
|**DMTREEOP_CHILDREN**|**0x00000001**|  
|**DMTREEOP_SIBLINGS**|**0x00000002**|  
|**DMTREEOP_PARENT**|**0x00000004**|  
|**DMTREEOP_SELF**|**0x00000008**|  
|**DMTREEOP_DESCENDANTS**|**0x00000010**|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

