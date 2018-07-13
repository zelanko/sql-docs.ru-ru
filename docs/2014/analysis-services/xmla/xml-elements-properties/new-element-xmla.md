---
title: Элемент New (XMLA) | Документация Майкрософт
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
- New Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#New
- microsoft.xml.analysis.new
- urn:schemas-microsoft-com:xml-analysis#New
helpviewer_keywords:
- New element
ms.assetid: 1321adcb-67f7-40f0-8f20-b17c1d3e3f17
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f93da2c5c9dab8b8d7542db68e70df67a87afbe8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203984"
---
# <a name="new-element-xmla"></a>Элемент New (XML для аналитики)
  Содержит новый место в файловой системе хранилища используется [папку](folder-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папка](folder-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `New` содержит UNC-путь, который заменяет значение элемента `Original`, содержащегося в родительском элементе `Folder` для всех восстанавливаемых или синхронизируемых объектов, соответственно, во время выполнения команды `Restore` или `Synchronize`. Значение элемента `Original` сравнивается со значением элемента `StorageLocation` для каждого куба, группы мер или секции, а в случае обнаружения соответствия значение этого элемента используется для обновления значения объекта `StorageLocation` во время восстановления или синхронизации.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервное копирование и восстановление объектов (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Original &#40;XML для Аналитики&#41;](original-element-xmla.md)   
 [Элемент RESTORE &#40;XML для Аналитики&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Элемент StorageLocation &#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
