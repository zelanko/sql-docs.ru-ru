---
title: Элемент ErrorConfiguration (XML для Аналитики) | Документы Microsoft
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
- ErrorConfiguration Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ErrorConfiguration
- urn:schemas-microsoft-com:xml-analysis#ErrorConfiguration
- microsoft.xml.analysis.errorconfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: 5e350f5f-3a14-49b4-80c0-208c61f336d5
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1ce9cf2dc862f187c1a9f9cb9e3403e01ade0cfa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101825"
---
# <a name="errorconfiguration-element-xmla"></a>Элемент ErrorConfiguration (XML для аналитики)
  Задает параметры обработки ошибок, возникающих во время [пакета](../xml-elements-commands/batch-element-xmla.md) или [процесс](../xml-elements-commands/process-element-xmla.md) операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Batch> <!-- or Process -->  
   ...  
   <ErrorConfiguration>  
      <KeyErrorLimit>...</KeyErrorLimit>  
      <KeyErrorLogFile>...</KeyErrorLogFile>  
      <KeyErrorAction>...</KeyErrorAction>  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
      <KeyNotFound>...</KeyNotFound>  
      <KeyDuplicate>...</KeyDuplicate>  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
      <NullKeyNotAllowed>...<NullKeyNotAllowed>  
   </ErrorConfiguration>  
   ...  
</Batch>  
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
|Родительские элементы|[Batch](../xml-elements-commands/batch-element-xmla.md), [Process](../xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|[KeyDuplicate](../../scripting/properties/keyduplicate-element-assl.md), [KeyErrorAction](../../scripting/objects/action-element-assl.md), [KeyErrorLimit](../../scripting/properties/keyerrorlimit-element-assl.md), [KeyErrorLimitAction](../../scripting/properties/keyerrorlimitaction-element-assl.md), [KeyErrorLogFile](../../scripting/objects/file-element-assl.md), [ KeyNotFound](../../scripting/properties/keynotfound-element-assl.md), [NullKeyConvertedToUnknown](../../scripting/properties/nullkeyconvertedtounknown-element-assl.md), [NullKeyNotAllowed](../../scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Структура данного элемента идентична структуре элемента `ErrorConfiguration` в языке ASSL. Дополнительные сведения о `ErrorConfiguration` элемент, в разделе [элемент ErrorConfiguration &#40;ASSL&#41;](../../scripting/objects/errorconfiguration-element-assl.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  