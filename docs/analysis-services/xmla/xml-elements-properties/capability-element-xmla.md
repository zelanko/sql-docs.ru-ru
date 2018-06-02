---
title: Элемент capability (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
ms.openlocfilehash: dca8f668f64ab8ced157cf817be1f9f8f6390133
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574986"
---
# <a name="capability-element-xmla"></a>Элемент Capability (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает на поддержку возможностей протокола в родительском объекте [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) элемент заголовка.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ProtocolCapabilities>  
   ...  
   <Capability>...</Capability>  
   ...  
</ProtocolCapabilities>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Возможность** элемент указывает, что определенные возможности, например двоичные операции или сжатие, поддерживается любое приложение, которое включено **ProtocolCapabilities** элемент заголовка в Заголовок SOAP SOAP-запроса или в экземпляре служб Analysis Services, которое включено **ProtocolCapabilities** элемент заголовка в заголовке SOAP SOAP-ответа. Значением элемента **Capability** является имя поддерживаемой возможности.  
  
 В следующей таблице перечислены возможности, поддерживаемые службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Имя возможности|Описание|  
|---------------------|-----------------|  
|sx|Поддержка двоичного XML|  
|xpress|Поддержка сжатия|  
  
## <a name="see-also"></a>См. также
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
