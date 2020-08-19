---
description: --(Комментарий) (расширения интеллектуального анализа данных)
title: --(Комментарий) (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 260a3f5c8a6d1badb90349396db6f2b716380aa7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431096"
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
  
## <a name="remarks"></a>Remarks  
 Этот оператор используется для однострочных или вложенных комментариев. Комментарии, вставляемые с помощью двойного дефиса, ограничиваются символом новой строки.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных типов комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40;dmx&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Косая черта-звездочка &#40;комментарии&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [Двойная косая черта &#40;комментарий&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-dmx.md)  
  
  
