---
title: "Косая черта звезда (комментарий) (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5bfaadd08f5a9aba145c754f281cf1d2c8e38496
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

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
 Многострочные комментарии должны обозначаться символами / * и \*/.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40; расширений интеллектуального анализа данных &#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Двойная косая черта &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/double-slash-comment-dmx.md)   
 [--&#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41; Сводка](../dmx/comment-dmx-summary.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-dmx.md)  
  
  

