---
title: Элемент warning (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 73662315d294cade8b344f8967923fe15e94f886
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576736"
---
# <a name="warning-element-xmla"></a>Элемент Warning (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит сведения о предупреждении, возвращенном экземпляром служб Analysis Services.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Message>  
   <Warning   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|ErrorCode|Обязательный атрибут типа **UnsignedInt** . Содержит числовой код возврата предупреждения.|  
|Severity|Необязательный атрибут типа **String** . Содержит серьезность предупреждения.|  
|Описание|Необязательный атрибут типа **String** . Содержит описательный текст предупреждения.|  
|Source|Необязательный атрибут типа **String** . Содержит имя компонента, который сформировал предупреждение.|  
|HelpFile|Необязательный атрибут типа **String** . Содержит путь или URL-адрес к файлу или разделу справки, в котором описывается предупреждение.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также
 [Элемент Error &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
