---
title: Элемент Error (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f223bff2dced01c2b3f954ca14242b1a35c93813
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036652"
---
# <a name="error-element-xmla"></a>Элемент Error (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит сведения об ошибке, возвращенные экземпляром служб Analysis Services.  
  
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
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Дочерние элементы|См. таблицу ниже.|  
  
|Предок|Дочерние элементы|  
|--------------|--------------------|  
|[Сообщение](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|None|  
|[Ячейка](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [строки](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Описание](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [источника](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|ErrorCode|Требуется **UnsignedInt** атрибут (только тогда, когда **сообщение** является родительским элементом.) Содержит числовой код возврата ошибки.|  
|Severity|Необязательный **строка** атрибут (только тогда, когда **сообщение** является родительским элементом.) Содержит серьезность ошибки.|  
|Описание|Необязательный **строка** атрибут (только тогда, когда **сообщение** является родительским элементом.) Содержит описательный текст ошибки.|  
|Source|Необязательный **строка** атрибут (только тогда, когда **сообщение** является родительским элементом.) Содержит имя компонента, который сформировал ошибку.|  
|HelpFile|Необязательный **строка** атрибут (только тогда, когда **сообщение** является родительским элементом.) Содержит путь или URL-адрес к файлу или разделу справки, в котором описывается ошибка.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также
 [Элемент warning &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
