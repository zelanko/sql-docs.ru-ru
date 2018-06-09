---
title: Элемент BackupRemotePartitions (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 33e81bd76e7f900a396b1f9bfbae808092a2877e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575086"
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
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|False|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элемент **BackupRemotePartitions** имеет значение **True**, в команду **Locations** должен включаться элемент **Location** , содержащий один или несколько элементов **Backup** , иначе возникает ошибка. Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также
 [Элемент Locations &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)   
 [Элемент Location &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
