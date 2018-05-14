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
ms.openlocfilehash: 92e9fa83f19384276abd7401fd809a56187c75b7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="capability-element-xmla"></a>Элемент Capability (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает на поддержку возможностей протокола в родительском элементе заголовка [ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md) .  
  
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
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ProtocolCapabilities](../../../analysis-services/xmla/xml-elements-headers/protocolcapabilities-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Возможность** элемент указывает, что определенные возможности, например двоичные операции или сжатие, поддерживается любое приложение, которое включено **ProtocolCapabilities** элемент заголовка в Заголовок SOAP SOAP-запроса или экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , включены **ProtocolCapabilities** элемент заголовка в заголовке SOAP SOAP-ответа. Значением элемента **Capability** является имя поддерживаемой возможности.  
  
 В следующей таблице перечислены возможности, поддерживаемые службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Имя возможности|Описание|  
|---------------------|-----------------|  
|sx|Поддержка двоичного XML|  
|xpress|Поддержка сжатия|  
  
## <a name="see-also"></a>См. также:  
 [Управление & #40; соединений и сеансов XML для Аналитики & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
