---
title: Введите элемент (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a080a1af46df731befc8ab66ce925b961be9b16
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051602"
---
# <a name="type-element-xmla"></a>Элемент Type (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет тип обработки, которые будут произведены методом [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о параметрах обработки, доступных для объектов в экземпляре служб Analysis Services, см. в разделе [обработка многомерной модели &#40;служб Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Значение **тип** может быть только одна из строк, перечисленных в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*ProcessFull*|Удаляет из задействованного объекта все данные, после чего выполняет обработку этого объекта.|  
|*ProcessAdd*|Добавляет к задействованному объекту новые данные.|  
|*ProcessUpdate*|Обновляет данные в задействованном объекте.|  
|*ProcessIndexes*|Создает или перестраивает индексы и агрегаты в задействованном объекте.|  
|*ProcessScriptCache*|Если куб обработан, сервер перестраивает кэш скрипта многомерных выражений. В противном случае возникнет ошибка.<br /><br /> **Примечание** применяется только к кубам.|  
|*ProcessData*|Выполняет обработку данных только в задействованном объекте.|  
|*ProcessDefault*|Определяет состояние задействованного объекта и выполняет обработку, соответствующую режиму этого объекта, с целью его полной оптимизации и перевода в полностью обработанное состояние.|  
|*ProcessClear*|Удаляет данные из задействованного объекта и всех связанных объектов.|  
|*ProcessStructure*|Выполняет обработку структуры только задействованного объекта.|  
|*ProcessClearStructureOnly*|Выполняет очистку данных только в задействованном объекте.|  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
