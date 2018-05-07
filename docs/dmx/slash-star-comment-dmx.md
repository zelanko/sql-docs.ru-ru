---
title: Косая черта звезда (комментарий) (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- commenting characters
- forward slash-asterisk character pairs
- /*...*/ (comment)
ms.assetid: 163976cc-aa47-4eda-bd98-03c1a397f80e
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 37858f818ec35e6eb68c13034fc8ca7e56dc0150
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="slash-star-comment-dmx"></a>Косая черта-звездочка (комментарий) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает строку текста, которая не должна выполняться службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Сервер не обрабатывает текст между символами комментария / * и \*/. Комментарии внутри инструкции языка расширений интеллектуального анализа данных могут быть вложенными, их можно включать в конце строки кода или вставлять отдельной строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Замечания  
 Многострочные комментарии необходимо отмечать сочетаниями символов /* и \*/.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40;расширений интеллектуального анализа данных&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также  
 [Двойная косая черта &#40;комментарий&#41; &#40;расширений интеллектуального анализа данных&#41;](../dmx/double-slash-comment-dmx.md)   
 [-- &#40;Комментарий&#41; &#40;расширений интеллектуального анализа данных&#41; Сводка](../dmx/comment-dmx-summary.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-dmx.md)  
  
  
