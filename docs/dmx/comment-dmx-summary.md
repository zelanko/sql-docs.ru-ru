---
title: "--(Комментарий) (расширения интеллектуального анализа данных) Сводка | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0ab3cef118685094ae96e02dcbf6b994e1157cd0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="---comment-dmx-summary"></a>--Сводка (комментарий) (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает строку текста, которая не должна выполняться службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Комментарии внутри инструкции языка расширений интеллектуального анализа данных могут быть вложенными, их можно включать в конце строки кода или вставлять отдельной строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Замечания  
 Этот оператор используется для однострочных или вложенных комментариев. Комментарии, вставляемые с помощью двойного дефиса, ограничиваются символом новой строки.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40; расширений интеллектуального анализа данных &#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Косая черта-звездочка &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/slash-star-comment-dmx.md)   
 [Двойная косая черта &#40; Комментарий &#41; &#40; расширений интеллектуального анализа данных &#41;](../dmx/double-slash-comment-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-dmx.md)  
  
  

