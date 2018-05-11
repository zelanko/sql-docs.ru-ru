---
title: Элемент RequestType (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cc420aa56d535c826bcff4b78739740e8e5f6bbe
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="requesttype-element-xmla"></a>Элемент RequestType (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет тип метаданных, возвращенный [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Обнаружение](../../../analysis-services/xmla/xml-elements-methods-discover.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **RequestType** определяет набор строк схемы, из которого **Discover** метод возвращает данные. Это перечисление ограничивается именами наборов строк схемы, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Дополнительные сведения о наборах строк схемы см. в разделе [наборы строк схемы служб Analysis](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md).  
  
> [!NOTE]  
>  **RequestType** перечисляет только имена набора строк схемы. Использование идентификатора GUID набора строк схемы приводит к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
