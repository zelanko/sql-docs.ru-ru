---
title: Элемент LogFileRollover (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 97a472f44cf840093d2b7f92bd7184e41561274a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="logfilerollover-element-assl"></a>Элемент LogFileRollover (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает, будет ли протоколирование данных [трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md) должен продолжаться выходные данные в новый файл или при достижении максимального размера файла журнала, указанного в [LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md) достигается.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|False|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Трассировки](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элементу **LogFileRollover** присвоено значение TRUE, то при превышении файлом журналов размера, указанного в элементе **LogFileSize** родительского элемента **Trace** , начинается новый журнал; в противном случае ведение журнала останавливается.  
  
 Элемент, соответствующий родителю параметра **LogFileRollover** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также  
 [Элемент traces & #40; ASSL & #41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
