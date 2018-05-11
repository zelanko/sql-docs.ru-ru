---
title: Элемент Password (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 488b406a6378853ecf34fce5405669e28420bde4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="password-element-xmla"></a>Элемент Password (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет пароль, который будет использоваться родительской [резервного копирования](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) или [восстановить](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) команду для шифрования или расшифрования файла резервной копии.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Резервное копирование](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [восстановления](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если при выполнении команды **Backup** не был включен элемент **Password** или он содержит пустую строку, то файл резервной копии не будет зашифрован.  
  
 Если при выполнении команды **Restore** не был включен элемент **Password** или он содержит пустую строку, то при попытке восстановления зашифрованного файла резервной копии возникнет ошибка.  
  
 Если при выполнении команды **Location** или **Backup** был включен элемент **Restore** , то для обычного и удаленного файлов резервной копии будет использован один и тот же элемент **Password** . Дополнительные сведения об удаленных файлах резервных копий см. в разделе [резервное копирование, восстановление и синхронизация баз данных &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Location &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
