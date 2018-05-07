---
title: SELECT FROM &lt;модели&gt;. SAMPLE_CASES (DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SAMPLE_CASES
- SELECT
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- SELECT FROM <model>.SAMPLE_CASES statement
- mining models [Analysis Services], sample cases
- sample cases [DMX]
- training mining models
ms.assetid: e7a34b9b-3562-4503-bfa7-dd9b12db480a
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 013b98a8f70d99810ba3032e3c0f3ac65db27acf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM &lt;модели&gt;. SAMPLE_CASES (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает образцы объектов, используемых для обучения модели интеллектуального анализа данных.  
  
 Для использования данной инструкции необходимо активировать детализацию при создании модели интеллектуального анализа данных. Дополнительные сведения об активации детализации см. в разделе [CREATE MINING MODEL &#40;расширений интеллектуального анализа данных&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;расширений интеллектуального анализа данных&#41;](../dmx/select-into-dmx.md), и [ALTER MINING STRUCTURE &#40;Расширений интеллектуального анализа данных&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 Необязательно. Целое число, указывающее количество возвращаемых строк.  
  
 *список выражений*  
 Идентификаторы связанных столбцов, перечисленные через запятую.  
  
 *model*  
 Идентификатор модели.  
  
 *Список условий*  
 Необязательно. Условия ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательно. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Замечания  
 Образцы вариантов могут формироваться, но не существовать фактически в обучающих данных. Возвращаемый вариант отображает заданный узел содержимого.  
  
 Несмотря на то что [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм кластеризации последовательностей является единственным [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм, который поддерживает использование SELECT FROM \<модели >. SAMPLE_CASES, алгоритмы других производителей могут также поддерживать ее.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выдаются столбцы для всех вариантов, которые использовались для обучения модели интеллектуального анализа данных Target Mail. С помощью [IsInNode &#40;расширений интеллектуального анализа данных&#41; ](../dmx/isinnode-dmx.md) функционировать в **ГДЕ** предложение возвращаются только варианты, связанные с узлом '000000003'. Строка узла хранится в столбце NODE_UNIQUE_NAME набора строк схемы.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>См. также  
 [ВЫБЕРИТЕ &AMP;#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&AMP;#41;](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
