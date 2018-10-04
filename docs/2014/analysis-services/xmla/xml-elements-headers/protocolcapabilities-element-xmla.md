---
title: Элемент ProtocolCapabilities (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProtocolCapabilities Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 12e4cac0c9846582c40213048e71c7f3793ff736
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219044"
---
# <a name="protocolcapabilities-element-xmla"></a>Элемент ProtocolCapabilities (XML для аналитики)
  Использует заголовок SOAP в сообщении SOAP-запроса для определения возможностей протокола между экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и клиентским приложением.  
  
 **пространство имен** http://schemas.microsoft.com/analysisservices/2003/engine  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
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
|Дочерние элементы|[Возможность](../xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `ProtocolCapabilities` позволяет клиентскому приложению в любой момент согласовать возможности протокола, например двоичного XML или поддержки сжатия, с экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Согласование протокола включает следующие шаги.  
  
1.  Клиентское приложение определяет возможности своего протокола путем отправки запроса SOAP, который включает в себя `ProtocolCapabilities` элемент как часть заголовка SOAP.  
  
2.  Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] получает и обрабатывает запрос SOAP.  
  
3.  Если экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеет требуемые возможности протокола, он отправляет ответ SOAP, включающий тот же элемент `ProtocolCapabilities`, который присутствовал в запросе SOAP, в результате чего протокол будет успешно согласован. В противном случае возможности протокола не согласуются и экземпляр возвращает ошибку SOAP.  
  
 После успешного согласования возможностей протокола, как долго клиентское приложение и [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используйте экземпляр определенного протокола зависит от того, является ли сеанс явным или неявным:  
  
-   Явный сеанс — это приложения, создается с помощью [BeginSession](session-element-xmla.md) элемент заголовка. Для явного сеанса, согласованный протокол используется, пока клиентское приложение не отправит новый `ProtocolCapabilities` элемент или не завершится сеанс.  
  
-   Неявный сеанс создается экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и не задается явно клиентским приложением при приеме запроса SOAP. В неявном сеансе согласованный протокол используется только до завершения запроса SOAP.  
  
 Возможности протокола не обязательно согласовывать явно. То есть клиентское приложение не имеет для включения `ProtocolCapabilities` элемент как часть запроса SOAP. Если запрос SOAP не включает элемент `ProtocolCapabilities`, экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] отвечает, используя формат запроса SOAP.  
  
## <a name="see-also"></a>См. также  
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](xml-elements-headers.md)  
  
  
