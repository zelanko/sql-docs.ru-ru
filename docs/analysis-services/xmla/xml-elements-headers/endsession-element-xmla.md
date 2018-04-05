---
title: Элемент EndSession (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EndSession Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EndSession
- urn:schemas-microsoft-com:xml-analysis#EndSession
- microsoft.xml.analysis.endsession
helpviewer_keywords:
- EndSession element
ms.assetid: e64f1da4-5c83-40a2-b15e-837f5451bafa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 274c56e96093da4e71614d1e32a4b2e3300d07cc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="endsession-element-xmla"></a>Элемент EndSession (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Использует заголовок SOAP в сообщении SOAP-запроса для завершения существующего сеанса в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
  
|Характеристика|Description|  
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
  
|attribute|Description|  
|---------------|-----------------|  
|SessionId|Необходимый атрибут типа **String** , идентифицирующий завершаемый сеанс. Для определения сеанса службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используют идентификатор GUID.|  
  
## <a name="remarks"></a>Remarks  
 **EndSession** входит элемент заголовка SOAP-запроса, отправленного в существующий, явно запущенный сеанс в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Если элемент заголовка **EndSession** отправлен, но содержит идентификатор недействительного сеанса, возвращается ошибка SOAP, указывающая, что сеанс не найден.  
  
## <a name="see-also"></a>См. также:  
 [Элемент BeginSession &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)   
 [Элемент Session &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [Управление &#40; соединений и сеансов XML для Аналитики &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
