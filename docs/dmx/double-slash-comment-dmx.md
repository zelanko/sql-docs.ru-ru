---
title: Двойная косая черта (комментарий) (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7f6e05ac728f6e1a9dda94dfcb07d26309b3e1f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68061676"
---
# <a name="double-slash-comment-dmx"></a>Двойная косая черта (комментарий) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает строку текста, которая не должна выполняться службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Комментарии внутри инструкции языка расширений интеллектуального анализа данных могут быть вложенными, их можно включать в конце строки кода или вставлять отдельной строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Remarks  
 Символы // используются только для однострочных комментариев. Комментарии, обозначенные символами //, разделяются символом новой строки.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных типов комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40;dmx&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также:  
 [Косая черта-звездочка &#40;комментарии&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [--&#40;комментарий&#41; &#40;&#41; сводные данные расширений интеллектуального анализа данных](../dmx/comment-dmx-summary.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)  
  
  
