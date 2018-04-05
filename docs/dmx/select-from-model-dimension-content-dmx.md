---
title: SELECT FROM &lt;модели&gt;. DIMENSION_CONTENT (DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SELECT
- FROM
- DIMENSION_CONTENT
dev_langs:
- DMX
helpviewer_keywords:
- mining models [Analysis Services], dimension content
- SELECT FROM <model>.DIMENSION_CONTENT statement
ms.assetid: 907fb3fb-2131-4a10-8635-2a39b9a805aa
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eea37242444142b217e7a792465553cfc316321d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="select-from-ltmodelgtdimensioncontent-dmx"></a>SELECT FROM &lt;модели&gt;. DIMENSION_CONTENT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Модель интеллектуального анализа данных можно использовать как измерение в кубе OLAP, причем каждый узел модели представлен как элемент измерения. **SELECT FROM \<модели >. Dimension_CONTENT** инструкция возвращает содержимое модели, которая подходит для использования в качестве измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.Dimension_CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 Необязательный параметр. Целое число, указывающее количество возвращаемых строк.  
  
 *список выражений*  
 Список связанных идентификаторов столбцов с разделителями-запятыми, полученных на основе набора строк схемы содержимого.  
  
 *model*  
 Идентификатор модели.  
  
 *Условное выражение*  
 Необязательный параметр. Условие ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательный параметр. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Remarks  
 Поставщики алгоритмов определяют, какое содержимое возвращается и как его организовать. Например, поставщик может ограничить количество узлов, описываемых в содержимом измерения.  
  
 Следующая таблица перечисляет столбцы, которые можно запросить для содержимого измерения, и функцию, которую каждый столбец выполняет как измерение интеллектуального анализа данных.  
  
|столбец набора строк CONTENT|Функция в измерении интеллектуального анализа данных|  
|---------------------------|---------------------------------------|  
|ATTRIBUTE_NAME|Свойство элемента.|  
|NODE_NAME|Свойство элемента.|  
|NODE_UNIQUE_NAME|Ключевой атрибут.|  
|NODE_TYPE|Свойство элемента.|  
|NODE_CAPTION|Столбец CaptionColumn для **ключ** атрибута.|  
|CHILDREN_CARDINALITY|Свойство элемента.|  
|PARENT_UNIQUE_NAME|Атрибут RelatedAttribute для **ключ** атрибут (ParentAttribute в иерархии родители потомки).|  
|NODE_DESCRIPTION|Свойство элемента.|  
|NODE_RULE|Свойство элемента.|  
|MARGINAL_RULE|Свойство элемента.|  
|NODE_PROBABILITY|Свойство элемента.|  
|MARGINAL_PROBABILITY|Свойство элемента.|  
|NODE_SUPPORT|Свойство элемента.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Description  
 В примере выбираются все столбцы из содержимого модели `[TM Decision Tree]`, которая подходит для использования в качестве измерения.  
  
### <a name="code"></a>Код  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>См. также:  
 [ВЫБЕРИТЕ &#40; РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ &#41;](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
