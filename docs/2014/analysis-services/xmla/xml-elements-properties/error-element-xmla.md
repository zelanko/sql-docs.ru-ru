---
title: Элемент Error (XML для Аналитики) | Документы Microsoft
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
- Error Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 35c3b1ea4ee852365933d5a95d1f7ca822eff0fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100934"
---
# <a name="error-element-xmla"></a>Элемент Error (XML для аналитики)
  Содержит сведения об ошибке, возвращенные экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Сообщение](message-element-xmla.md)|  
  
## <a name="child-elements"></a>Дочерние элементы  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[Сообщение](message-element-xmla.md)|None|  
|[Ячейка](cell-element-mddataset-xmla.md), [строки](description-element-xmla.md), [ErrorCode](errorcode-element-xmla.md), [HelpFile](file-element-xmla.md), [источника](source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|ErrorCode|Требуется `UnsignedInt` атрибут (только если `Message` является родительским элементом.) Содержит числовой код возврата ошибки.|  
|Severity|Необязательный `String` атрибут (только если `Message` является родительским элементом.) Содержит серьезность ошибки.|  
|Описание|Необязательный `String` атрибут (только если `Message` является родительским элементом.) Содержит описательный текст ошибки.|  
|Source|Необязательный `String` атрибут (только если `Message` является родительским элементом.) Содержит имя компонента, который сформировал ошибку.|  
|HelpFile|Необязательный `String` атрибут (только если `Message` является родительским элементом.) Содержит путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Элемент warning &#40;XML для Аналитики&#41;](warning-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  