---
title: Элемент SPID (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39f4391ef919ad3de5233df078535b34691e1424
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036692"
---
# <a name="spid-element-xmla"></a>Элемент SPID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет активный идентификатор серверного процесса (SPID), в котором должен выполняться родительский [отменить](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cancel>  
   ...  
   <SPID>...</SPID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Отмена](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **SPID** элемент представляет процесс сервера идентификатор (SPID), используемый в данном сеансе в экземпляре служб Analysis Services.  
  
## <a name="see-also"></a>См. также
 [Элемент CancelAssociated &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Элемент ConnectionID &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Элемент SessionID &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
