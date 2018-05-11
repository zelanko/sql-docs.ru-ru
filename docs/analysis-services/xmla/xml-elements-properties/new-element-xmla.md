---
title: Новый элемент (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71aa322b198dd774634736e03cb82aac1aaa58cd
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="new-element-xmla"></a>Элемент New (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит место хранения новой файловой системе используется [папки](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) элемента.  
  
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
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папка](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **New** элемент содержит UNC-путь, который заменяет значение **исходного** элемента, содержащегося в родительском **папки** элемент для всех объектов, восстановления или синхронизации соответственно, во время **восстановить** или **Synchronize** команды. Значение **исходного** элемент сравнивается с значение **StorageLocation** элемент для каждого куба, группы мер или секции и, если соответствие найдено, значение этого элемента используется для обновления **StorageLocation** объекта во время восстановления или синхронизации.  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервное копирование и восстановление объектов (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Исходный элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)   
 [Восстановить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Элемент StorageLocation & #40; ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Синхронизировать элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
