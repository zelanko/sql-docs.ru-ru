---
title: Элемент BackupRemotePartitions (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 565fc78cc4a0aa0fe04c8d8196689a0c9cacb82b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="backupremotepartitions-element-xmla"></a>Элемент BackupRemotePartitions (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет, является ли родительский [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) команда создает резервную копию удаленных секций, связанных с объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup>  
   ...  
   <BackupRemotePartitions>...</BackupRemotePartitions>  
   ...  
</Backup>  
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
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элемент **BackupRemotePartitions** имеет значение **True**, в команду **Locations** должен включаться элемент **Location** , содержащий один или несколько элементов **Backup** , иначе возникает ошибка. Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных & #40; XML для Аналитики & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Locations &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)   
 [Элемент Location &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
