---
title: Элемент BeginSession (XML для Аналитики) | Документы Microsoft
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
- BeginSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 2982709512433e5a6b87929f3a4efba4f77138b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100482"
---
# <a name="beginsession-element-xmla"></a>Элемент BeginSession (XML для аналитики)
  Использует заголовок SOAP в сообщении SOAP-запроса для запуска нового сеанса в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
  
## <a name="remarks"></a>Примечания  
 Элемент заголовка `BeginSession` представляет собой часть SOAP-запроса, отправленного в экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], и явно запускает в экземпляре новый сеанс. Заголовок SOAP, возвращенный в ответе SOAP содержит [сеанса](session-element-xmla.md) элемент, который идентифицирует новый сеанс. Этот идентификатор нового сеанса сохраняется и передается в последующих SOAP-запросах с помощью элемента заголовка `Session`.  
  
 Если элемент заголовка `BeginSession` не передается, явного запуска сеанса не происходит. Если сеанс не был явно запущен, отсутствует возможность управлять транзакциями в этом сеансе. Другими словами, нельзя использовать следующий код XML для аналитики (XMLA) команды: [BeginTransaction](../xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xml-elements-commands/committransaction-element-xmla.md), и [RollbackTransaction](../xml-elements-commands/rollbacktransaction-element-xmla.md). Все методы и команды XMLA, вызываемые на выполнение в неявно запущенном сеансе, рассматриваются как неразрывные транзакции.  
  
## <a name="see-also"></a>См. также  
 [Элемент EndSession &#40;XML для Аналитики&#41;](endsession-element-xmla.md)   
 [Элемент Session &#40;XML для Аналитики&#41;](session-element-xmla.md)   
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](xml-elements-headers.md)  
  
  