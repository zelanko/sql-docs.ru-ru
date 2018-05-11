---
title: Элемент CurrentStorageMode (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b8a2b612e50b072c4b12caac321e75957ea3c952
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="currentstoragemode-element-assl"></a>Элемент CurrentStorageMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет текущий режим хранения для родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension> <!-- or Partition -->  
   <CurrentStorageMode>...</CurrentStorageMode>  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*ROLAP*|  
|Количество элементов|0—1: необязательный элемент, который может встречаться один раз или вообще не встречаться.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Измерение](../../../analysis-services/scripting/objects/dimension-element-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент **CurrentStorageMode** определяет режим хранения, который используется в настоящее время для упреждающего кэширования и применим ко всем атрибутам родительского элемента.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*MOLAP*|Родительский элемент использует многомерное хранилище OLAP (MOLAP).|  
|*ROLAP*|Родительский элемент использует реляционное хранилище OLAP (ROLAP).|  
|*HOLAP*|Родительский элемент использует гибридное хранилище OLAP (HOLAP).<br /><br /> Примечание: Это значение допустимо только для [секции](../../../analysis-services/scripting/objects/partition-element-assl.md) от родительского элемента.|  
  
 Перечисление, соответствующее разрешенным значениям **CurrentStorageMode** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.StorageMode>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
