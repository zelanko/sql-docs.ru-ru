---
title: SELECT FROM &lt;модели&gt;. DIMENSION_CONTENT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29f730f0bdff985ffceb849c429e5d1b02f70d5f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992628"
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
  
 *Выражение условия*  
 Необязательный параметр. Условие ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательный параметр. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Примечания  
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
  
### <a name="description"></a>Описание  
 В примере выбираются все столбцы из содержимого модели `[TM Decision Tree]`, которая подходит для использования в качестве измерения.  
  
### <a name="code"></a>Код  
  
```  
SELECT *   
FROM [TM Decision Tree].Dimension_Content  
```  
  
## <a name="see-also"></a>См. также  
 [ВЫБЕРИТЕ &AMP;#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&AMP;#41;](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкций по обработке данных](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
