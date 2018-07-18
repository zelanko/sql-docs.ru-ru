---
title: Введите элемент (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 336266b8290f1a4eb10d200d8c1c31bf00f96879
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193784"
---
# <a name="type-element-xmla"></a>Элемент Type (XML для аналитики)
  Определяет тип обработки, которые будут произведены методом [процесс](../xml-elements-commands/process-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Процесс](../xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о параметрах обработки, доступных для объектов в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], см. в разделе [обработку объекта многомерных моделей](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Значением элемента `Type` может быть только одна из строк в следующей таблице.  
  
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
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
