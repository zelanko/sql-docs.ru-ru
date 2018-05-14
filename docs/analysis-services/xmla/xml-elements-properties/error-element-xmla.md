---
title: Элемент Error (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 48413d3b21f2a1fce57e30956f5da4b2fe80d404
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="error-element-xmla"></a>Элемент Error (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит сведения об ошибке, возвращенные экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|None|  
|[Cell](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [row](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Description](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|ErrorCode|Требуется **UnsignedInt** атрибут (только если **сообщение** является родительским элементом.) Содержит числовой код возврата ошибки.|  
|Severity|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит серьезность ошибки.|  
|Описание|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит описательный текст ошибки.|  
|Source|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит имя компонента, который сформировал ошибку.|  
|HelpFile|Необязательный **строка** атрибут (только если **сообщение** является родительским элементом.) Содержит путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка.|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Элемент warning & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
