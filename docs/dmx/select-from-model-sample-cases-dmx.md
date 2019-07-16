---
title: SELECT FROM &lt;модели&gt;. SAMPLE_CASES (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0838c688b0518bf1fc7ed6c5d65c3ef03d0a7aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928310"
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM &lt;модели&gt;. SAMPLE_CASES (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает образцы объектов, используемых для обучения модели интеллектуального анализа данных.  
  
 Для использования данной инструкции необходимо активировать детализацию при создании модели интеллектуального анализа данных. Дополнительные сведения о включении детализации см. в разделе [CREATE MINING MODEL &#40;расширений интеллектуального анализа данных&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-into-dmx.md), и [ALTER MINING STRUCTURE &#40;Расширений интеллектуального анализа данных&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 Необязательный параметр. Целое число, указывающее количество возвращаемых строк.  
  
 *список выражений*  
 Идентификаторы связанных столбцов, перечисленные через запятую.  
  
 *model*  
 Идентификатор модели.  
  
 *Список условий*  
 Необязательный параметр. Условия ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательный параметр. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Примечания  
 Образцы вариантов могут формироваться, но не существовать фактически в обучающих данных. Возвращаемый вариант отображает заданный узел содержимого.  
  
 Несмотря на то что [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм кластеризации последовательностей является единственным [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм, который поддерживает использование SELECT FROM \<модели >. SAMPLE_CASES, алгоритмы сторонних могут также поддерживать ее.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выдаются столбцы для всех вариантов, которые использовались для обучения модели интеллектуального анализа данных Target Mail. С помощью [IsInNode &#40;расширений интеллектуального анализа данных&#41; ](../dmx/isinnode-dmx.md) работать в **ГДЕ** предложение возвращаются только варианты, связанные с узлом '000000003'. Строка узла хранится в столбце NODE_UNIQUE_NAME набора строк схемы.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>См. также  
 [ВЫБЕРИТЕ &#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&#41;](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкций по обработке данных](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
