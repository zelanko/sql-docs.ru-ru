---
title: Элемент Error (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
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
- Error Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e0d513dc324fe6f1efc857a03bf231d06481c10c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="error-element-xmla"></a>Элемент Error (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Содержит сведения об ошибке, возвращенные экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
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
|Родительские элементы|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Дочерние элементы|См. в следующей таблице.|  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|None|  
|[Ячейка](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [строки](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Описание](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [источника](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Требуется **UnsignedInt** атрибут (только если **сообщение** является родительским элементом.) Содержит числовой код возврата ошибки.|  
|Severity|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит серьезность ошибки.|  
|Description|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит описательный текст ошибки.|  
|Source|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит имя компонента, который сформировал ошибку.|  
|HelpFile|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Элемент warning &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
