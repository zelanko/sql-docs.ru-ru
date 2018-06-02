---
title: Элемент Folders (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 803ec660944663c7f40f1b7c9dddc118b8b6b76c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575406"
---
# <a name="folders-element-xmla"></a>Элемент Folders (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию элементов [Folder](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) , которая используется родительским элементом [Location](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) при выполнении команды [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) или [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Location>  
   ...  
   <Folders>  
      <Folder>...</Folder>  
   </Folders>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|нет (коллекция)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Расположение](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Дочерние элементы|[Папка](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также
 [Элемент RESTORE &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
