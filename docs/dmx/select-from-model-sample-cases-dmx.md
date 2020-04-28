---
title: Выберите из &lt;модели&gt;. SAMPLE_CASES (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e0838c688b0518bf1fc7ed6c5d65c3ef03d0a7aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928310"
---
# <a name="select-from-ltmodelgtsample_cases-dmx"></a>Выберите из &lt;модели&gt;. SAMPLE_CASES (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает образцы объектов, используемых для обучения модели интеллектуального анализа данных.  
  
 Для использования данной инструкции необходимо активировать детализацию при создании модели интеллектуального анализа данных. Дополнительные сведения о включении детализации см. в статьях [Создание модели интеллектуального анализа данных &#40;&#41;расширений ](../dmx/create-mining-model-dmx.md)интеллектуального анализа данных, [SELECT INTO &#40;&#41;расширений интеллектуального ](../dmx/select-into-dmx.md)анализа данных и [ALTER MINING STRUCTURE &#40;DMX ](../dmx/alter-mining-structure-dmx.md)  
  
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
  
 *для базы данных модели*  
 Идентификатор модели.  
  
 *список условий*  
 Необязательный параметр. Условия ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательный параметр. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Remarks  
 Образцы вариантов могут формироваться, но не существовать фактически в обучающих данных. Возвращаемый вариант отображает заданный узел содержимого.  
  
 Хотя алгоритм [!INCLUDE[msCoName](../includes/msconame-md.md)] кластеризации последовательностей является единственным [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмом, поддерживающим использование \<SELECT из модели>. SAMPLE_CASES, сторонние алгоритмы также могут их поддерживать.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выдаются столбцы для всех вариантов, которые использовались для обучения модели интеллектуального анализа данных Target Mail. Использование функции [IsInNode &#40;расширений интеллектуального анализа данных&#41;](../dmx/isinnode-dmx.md) в предложении **WHERE** возвращает только варианты, связанные с узлом "000000003". Строка узла хранится в столбце NODE_UNIQUE_NAME набора строк схемы.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>См. также:  
 [ВЫБОР &#40;&#41;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
