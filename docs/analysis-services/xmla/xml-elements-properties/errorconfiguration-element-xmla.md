---
title: Элемент ErrorConfiguration (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- ErrorConfiguration Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ErrorConfiguration
- urn:schemas-microsoft-com:xml-analysis#ErrorConfiguration
- microsoft.xml.analysis.errorconfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: 5e350f5f-3a14-49b4-80c0-208c61f336d5
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a746b60020b10c6266264b76654a2c424fc34d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="errorconfiguration-element-xmla"></a>Элемент ErrorConfiguration (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Задает параметры обработки ошибок, возникающих во время [пакета](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) или [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) операции.  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md), [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|[KeyDuplicate](../../../analysis-services/scripting/properties/keyduplicate-element-assl.md), [KeyErrorAction](../../../analysis-services/scripting/properties/keyerroraction-element-assl.md), [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md), [KeyErrorLimitAction](../../../analysis-services/scripting/properties/keyerrorlimitaction-element-assl.md), [KeyErrorLogFile](../../../analysis-services/scripting/properties/keyerrorlogfile-element-assl.md), [ KeyNotFound](../../../analysis-services/scripting/properties/keynotfound-element-assl.md), [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md), [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Структура данного элемента идентична структуре элемента **ErrorConfiguration** в языке ASSL. Дополнительные сведения о **ErrorConfiguration** элемент, в разделе [элемент ErrorConfiguration &#40;ASSL&#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
