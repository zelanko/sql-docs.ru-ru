---
title: Элемент Session (XML для Аналитики) | Документы Microsoft
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
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4be4778be16da0271e2f46643a165864d679e8ff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102072"
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
  
-   Ответ SOAP, который содержит [BeginSession](session-element-xmla.md) элемент заголовка SOAP.  
  
-   SOAP-запрос на идентификацию сеанса, в которой будет выполняться [Discover](../xml-elements-methods-discover.md) или [Execute](../xml-elements-methods-execute.md) метод.  
  
 Идентификатор сеанса не гарантирует того, что сеанс остается допустимым. У сеанса, заданного в элементе `Session`, может истечь срок действия. Например, срок действия сеанса может истечь, если будет превышено время ожидания или произойдет отключение соединения, связанного с этим сеансом. Если время сеанса истекает и он становится недействительным, служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] завершает сеанс и выполняет откат текущих транзакций. Все SOAP-сообщения, отправленные с идентификатором недействительного сеанса, возвращают ошибку SOAP, указывающую, что заданный сеанс не найден.  
  
 Если элемент `Session` не был послан в сообщении-запросе SOAP, то экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] скрыто запускает сеанс на время выполнения вызова метода `Discover` или `Execute`, а после его завершения завершает данный сеанс.  
  
## <a name="see-also"></a>См. также  
 [Элемент EndSession &#40;XML для Аналитики&#41;](endsession-element-xmla.md)   
 [Управление соединениями и сеансами &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Заголовки &#40;XML для Аналитики&#41;](xml-elements-headers.md)  
  
  