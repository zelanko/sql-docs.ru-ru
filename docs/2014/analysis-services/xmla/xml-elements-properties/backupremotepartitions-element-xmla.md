---
title: Элемент BackupRemotePartitions (XML для Аналитики) | Документы Microsoft
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
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: c32fd50514e96fee8de289666d8e559a78fe985b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194570"
---
# <a name="backupremotepartitions-element-xmla"></a>Элемент BackupRemotePartitions (XML для аналитики)
  Определяет, является ли родительский [резервного копирования](../xml-elements-commands/backup-element-xmla.md) команда создает резервную копию удаленных секций, связанных с объектом.  
  
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
 Если элемент `BackupRemotePartitions` имеет значение `True`, в команду `Locations` должен включаться элемент `Location`, содержащий один или несколько элементов `Backup`, иначе возникает ошибка. Дополнительные сведения о резервном копировании и восстановлении удаленных секций см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Locations &#40;XML для Аналитики&#41;](locations-element-xmla.md)   
 [Элемент Location &#40;XML для Аналитики&#41;](location-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  