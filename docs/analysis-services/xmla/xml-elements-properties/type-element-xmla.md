---
title: Введите элемент (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 363b89eddf7794174689c0d6df7805328c88eb70
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-xmla"></a>Элемент Type (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Определяет тип обработки, выполняемой по [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о параметрах обработки, доступных для объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], в разделе [обработка многомерной модели &#40; Службы Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Значение **тип** элемента ограничивается одной из строк, перечисленных в следующей таблице.  
  
|Значение|Description|  
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
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
