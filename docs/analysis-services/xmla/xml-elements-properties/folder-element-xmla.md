---
title: Элемент Folder (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a13ac1689c58519a6e8d1ac06cacc8357570b75
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="folder-element-xmla"></a>Элемент Folder (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит место хранения файловой системы должны быть обновлены в [расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) во время выполнения [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Folders>  
   ...  
   <Folder>  
      <Original>...</Original>  
      <New>...</New>  
   </Folder>  
   ...  
</Folders>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Папки](../../../analysis-services/xmla/xml-elements-properties/folders-element-xmla.md)|  
|Дочерние элементы|[Новый](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md), [исходного](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 При указании элемента **Folder** он изменяет места хранения объектов, содержащихся в файле резервной копии (для команд **Restore** ) или в базе данных на экземпляре источника (для команд **Synchronize** ), если их значения совпадают со значением элемента **Original** . Каждое такое значение заменяется значением элемента **New** .  
  
 Дополнительные сведения о резервном копировании и восстановлении объектов см. в разделе [резервное копирование, восстановление и синхронизация баз данных & #40; XML для Аналитики & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент StorageLocation & #40; ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
