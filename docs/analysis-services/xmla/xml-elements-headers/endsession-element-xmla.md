---
title: Элемент EndSession (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 898e36720f633d929891f1b842a2442fa39ba288
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="endsession-element-xmla"></a>Элемент EndSession (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Использует SOAP-заголовок в сообщении SOAP-запроса для завершения существующего сеанса в экземпляре служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|Нет|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|SessionId|Необходимый атрибут типа **String** , идентифицирующий завершаемый сеанс. Для определения сеанса службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используют идентификатор GUID.|  
  
## <a name="remarks"></a>Примечания  
 **EndSession** входит элемент заголовка SOAP-запроса, отправленного в существующий, явно запущенный сеанс в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Если элемент заголовка **EndSession** отправлен, но содержит идентификатор недействительного сеанса, возвращается ошибка SOAP, указывающая, что сеанс не найден.  
  
## <a name="see-also"></a>См. также  
 [Элемент BeginSession & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [Элемент Session & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [Управление & #40; соединений и сеансов XML для Аналитики & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
