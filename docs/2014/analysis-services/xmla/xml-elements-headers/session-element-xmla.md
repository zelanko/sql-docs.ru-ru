---
title: Элемент Session (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Session Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a2f18754a2ef7d44a2a85bb9da78378bc631ecd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080394"
---
# <a name="session-element-xmla"></a>Элемент Session (XML для аналитики)
  Использует заголовок SOAP в сообщении SOAP-запроса, чтобы идентифицировать существующий явный сеанс на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|SessionId|Необходимый атрибут типа `String`, идентифицирующий используемый сеанс. Для определения сеанса службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] используют идентификатор GUID.|  
  
## <a name="remarks"></a>Примечания  
 Элемент заголовка `Session` определяет существующий, явно запущенный сеанс экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Элемент `Session` является частью заголовка SOAP для следующих типов сообщений.  
  
-   Ответ SOAP, содержащий [BeginSession](session-element-xmla.md) элемент заголовка SOAP.  
  
-   SOAP-запрос на идентификацию сеанса, в которой будет выполняться [Discover](../xml-elements-methods-discover.md) или [Execute](../xml-elements-methods-execute.md) метод.  
  
 Идентификатор сеанса не гарантирует того, что сеанс остается допустимым. У сеанса, заданного в элементе `Session`, может истечь срок действия. Например, срок действия сеанса может истечь, если будет превышено время ожидания или произойдет отключение соединения, связанного с этим сеансом. Если время сеанса истекает и он становится недействительным, служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] завершает сеанс и выполняет откат текущих транзакций. Все SOAP-сообщения, отправленные с идентификатором недействительного сеанса, возвращают ошибку SOAP, указывающую, что заданный сеанс не найден.  
  
 Если элемент `Session` не был послан в сообщении-запросе SOAP, то экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] скрыто запускает сеанс на время выполнения вызова метода `Discover` или `Execute`, а после его завершения завершает данный сеанс.  
  
## <a name="see-also"></a>См. также  
 [Элемент EndSession &#40;XML для Аналитики&#41;](endsession-element-xmla.md)   
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](xml-elements-headers.md)  
  
  
