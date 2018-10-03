---
title: Элемент BackupRemotePartitions (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- BackupRemotePartitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.backupremotepartitions
- http://schemas.microsoft.com/analysisservices/2003/engine#BackupRemotePartitions
- urn:schemas-microsoft-com:xml-analysis#BackupRemotePartitions
helpviewer_keywords:
- BackupRemotePartitions element
ms.assetid: bd68bcf9-b324-4fa8-b6e5-1f5531f9992c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e18d01ec48264d735a111bc002ca92b08c7b374
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108193"
---
# <a name="backupremotepartitions-element-xmla"></a>Элемент BackupRemotePartitions (XML для аналитики)
  Определяет ли родительский [резервного копирования](../xml-elements-commands/backup-element-xmla.md) команда создает резервные копии удаленных секций, связанных с объектом.  
  
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
|Родительские элементы|[Резервное копирование](../xml-elements-commands/backup-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если элемент `BackupRemotePartitions` имеет значение `True`, в команду `Locations` должен включаться элемент `Location`, содержащий один или несколько элементов `Backup`, иначе возникает ошибка. Дополнительные сведения о резервном копировании и восстановлении удаленных секций, см. в разделе [резервного копирования, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Locations &#40;XML для Аналитики&#41;](locations-element-xmla.md)   
 [Элемент Location &#40;XML для Аналитики&#41;](location-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
