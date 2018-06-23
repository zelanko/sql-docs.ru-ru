---
title: Элемент ProtocolCapabilities (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 0243e0050111c0bc478f17403f3014fc619d9a43
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097345"
---
# <a name="protocolcapabilities-element-xmla"></a>Элемент ProtocolCapabilities (XML для аналитики)
  Использует заголовок SOAP в сообщении SOAP-запроса для определения возможностей протокола между экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и клиентским приложением.  
  
 **Пространство имен** http://schemas.microsoft.com/analysisservices/2003/engine  
  
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
  
1.  Клиентское приложение определяет возможности своего протокола путем отправки запроса SOAP, который включает в себя `ProtocolCapabilities` как часть заголовка SOAP.  
  
2.  Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] получает и обрабатывает запрос SOAP.  
  
3.  Если экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеет требуемые возможности протокола, он отправляет ответ SOAP, включающий тот же элемент `ProtocolCapabilities`, который присутствовал в запросе SOAP, в результате чего протокол будет успешно согласован. В противном случае возможности протокола не согласуются и экземпляр возвращает ошибку SOAP.  
  
 После успешного согласования возможностей протокола длительность клиентское приложение и [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используйте экземпляр определенного протокола зависит от сеанса явной или неявной:  
  
-   Явный сеанс является запрос, который создается с помощью [BeginSession](session-element-xmla.md) элемент заголовка. В явном сеансе протокол используется, пока клиентское приложение не отправит новый `ProtocolCapabilities` элемента или окончания сеанса.  
  
-   Неявный сеанс создается экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и не задается явно клиентским приложением при приеме запроса SOAP. В неявном сеансе согласованный протокол используется только до завершения запроса SOAP.  
  
 Возможности протокола не обязательно согласовывать явно. То есть, клиентское приложение не имеет для включения `ProtocolCapabilities` как часть запроса SOAP. Если запрос SOAP не включает элемент `ProtocolCapabilities`, экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] отвечает, используя формат запроса SOAP.  
  
## <a name="see-also"></a>См. также  
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](xml-elements-headers.md)  
  
  