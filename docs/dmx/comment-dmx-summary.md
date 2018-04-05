---
title: --(Комментарий) (расширения интеллектуального анализа данных) Сводка | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
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
- double hyphens
- -- (comment character)
ms.assetid: 487b580b-5b81-4e52-8868-4fa809e4ef58
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 40b4189e6ce20c49ad7aab24b53ea41900b022f5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="---comment-dmx-summary"></a>--Сводка (комментарий) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 Дополнительные сведения об использовании различных комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40; расширений интеллектуального анализа данных &#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Косая черта-звездочка &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/slash-star-comment-dmx.md)   
 [Двойная косая черта &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/double-slash-comment-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-dmx.md)  
  
  
