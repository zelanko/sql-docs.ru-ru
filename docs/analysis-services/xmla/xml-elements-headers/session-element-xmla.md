---
title: Элемент Session (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 02b4c93919e6354a59aad9b42a4f6dc8373c880f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577506"
---
# <a name="session-element-xmla"></a>Элемент Session (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Использует заголовок SOAP в сообщении SOAP-запроса, чтобы идентифицировать существующий явный сеанс на экземпляре служб Analysis Services.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|SessionId|Необходимый атрибут типа **String** , идентифицирующий используемый сеанс. Для определения сеанса службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используют идентификатор GUID.|  
  
## <a name="remarks"></a>Примечания  
 **Сеанса** элемент заголовка определяет существующий, явно запущенный сеанс на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Элемент **Session** является частью заголовка SOAP для следующих типов сообщений.  
  
-   Ответ SOAP, который содержит [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) элемент заголовка SOAP.  
  
-   SOAP-запрос на идентификацию сеанса, в которой будет выполняться [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.  
  
 Идентификатор сеанса не гарантирует того, что сеанс остается допустимым. У сеанса, заданного в элементе **Session** , может истечь срок действия. Например, срок действия сеанса может истечь, если будет превышено время ожидания или произойдет отключение соединения, связанного с этим сеансом. Если время сеанса истекает и он становится недействительным, служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] завершает сеанс и выполняет откат текущих транзакций. Все SOAP-сообщения, отправленные с идентификатором недействительного сеанса, возвращают ошибку SOAP, указывающую, что заданный сеанс не найден.  
  
 Если **сеанса** элемент не отправляются как часть запроса SOAP, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр неявно начинает сеанс в течение **Discover** или **Execute** метод, а после его завершения завершает данный сеанс после завершения вызова метода.  
  
## <a name="see-also"></a>См. также
 [Элемент EndSession &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
