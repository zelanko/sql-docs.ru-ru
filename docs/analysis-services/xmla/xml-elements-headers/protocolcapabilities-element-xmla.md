---
title: "Элемент ProtocolCapabilities (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ProtocolCapabilities Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords: ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 42ff93dce6b71f7cfd69ed85d92c4c4f7912faee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="protocolcapabilities-element-xmla"></a>Элемент ProtocolCapabilities (XML для аналитики)
  Использует заголовок SOAP в сообщении SOAP-запроса для определения возможностей протокола между экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и клиентским приложением.  
  
 **Пространство имен**`http://schemas.microsoft.com/analysisservices/2003/engine`  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Возможность](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **ProtocolCapabilities** элемент позволяет клиентским приложениям согласовать возможности протокола, например двоичного XML или поддержки сжатия с [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра в любое время. Согласование протокола включает следующие шаги.  
  
1.  Клиентское приложение определяет возможности своего протокола с помощью отправки запроса SOAP, включающего элемент **ProtocolCapabilities** , как часть заголовка SOAP.  
  
2.  Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] получает и обрабатывает запрос SOAP.  
  
3.  Если [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возможности протокола, который содержит экземпляр, он отправляет ответ SOAP, включающий тот же **ProtocolCapabilities** элемент, отправляемых в запросе SOAP, а протокол была успешно согласован. В противном случае возможности протокола не согласуются и экземпляр возвращает ошибку SOAP.  
  
 После успешного согласования возможностей протокола длительность клиентское приложение и [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используйте экземпляр определенного протокола зависит от сеанса явной или неявной:  
  
-   Явный сеанс является запрос, который создается с помощью [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) элемент заголовка. В явном сеансе протокол используется, пока клиентское приложение не отправит новый элемент **ProtocolCapabilities** или не завершится сеанс.  
  
-   Неявный сеанс создается экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и не задается явно клиентским приложением при приеме запроса SOAP. В неявном сеансе согласованный протокол используется только до завершения запроса SOAP.  
  
 Возможности протокола не обязательно согласовывать явно. То есть клиентскому приложению не обязательно включать элемент **ProtocolCapabilities** , как часть запроса. Если запрос SOAP не включает **ProtocolCapabilities** элемент, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр отвечает, используя тот же формат запроса SOAP.  
  
## <a name="see-also"></a>См. также:  
 [Управление &#40; соединений и сеансов XML для Аналитики &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
