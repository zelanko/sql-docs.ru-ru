---
title: Элемент BeginSession (XML для Аналитики) | Документы Microsoft
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
- BeginSession Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b35ff5467daa888cfc9eefa47a7e2cf48b037946
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="beginsession-element-xmla"></a>Элемент BeginSession (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Использует заголовок SOAP в сообщении SOAP-запроса для запуска нового сеанса в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <BeginSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis" />  
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
  
## <a name="remarks"></a>Remarks  
 **BeginSession** элемент заголовка является частью SOAP-запроса, отправленного [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр и явно запускает новый сеанс на экземпляре. Заголовок SOAP, возвращенный в ответе SOAP содержит [сеанса](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md) элемент, который идентифицирует новый сеанс. Этот идентификатор нового сеанса сохраняется и передается в последующих SOAP-запросах с помощью элемента заголовка **Session** .  
  
 Если элемент заголовка **BeginSession** не передается, явного запуска сеанса не происходит. Если сеанс не был явно запущен, отсутствует возможность управлять транзакциями в этом сеансе. Другими словами, нельзя использовать следующий код XML для аналитики (XMLA) команды: [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), и [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md). Все методы и команды XMLA, вызываемые на выполнение в неявно запущенном сеансе, рассматриваются как неразрывные транзакции.  
  
## <a name="see-also"></a>См. также:  
 [Элемент EndSession &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Элемент Session &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [Управление &#40; соединений и сеансов XML для Аналитики &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
