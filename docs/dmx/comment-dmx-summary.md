---
title: --(Комментарий) (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4f0f01b0dc3550c6b09e6c2342232e6b7c7fac8f
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969915"
---
# <a name="---comment-dmx-summary"></a>--(Комментарий) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Указывает строку текста, которая не должна выполняться службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Комментарии внутри инструкции языка расширений интеллектуального анализа данных могут быть вложенными, их можно включать в конце строки кода или вставлять отдельной строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Комментарии  
 Этот оператор используется для однострочных или вложенных комментариев. Комментарии, вставляемые с помощью двойного дефиса, ограничиваются символом новой строки.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных типов комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40;dmx&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также  
 [Косая черта-звездочка &#40;комментарии&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [Двойная косая черта &#40;комментарий&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)  
  
  
