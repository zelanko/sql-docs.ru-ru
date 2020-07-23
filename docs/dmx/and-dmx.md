---
title: И (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3cacd8fe2d80e6037cf83df9eea1fd112a4b05
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971837"
---
# <a name="and-dmx"></a>AND (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Выполняет логическое умножение двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение принимает значение TRUE, если оба аргумента имеют значение TRUE, в противном случае возвращает значение FALSE.  
  
## <a name="remarks"></a>Примечания  
 Оба аргумента приводятся к значениям логического типа (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое умножение. В приведенной ниже таблице показаны результаты, соответствующие различным сочетаниям значений аргументов:  
  
|Если Expression1 равно|Если Expression2 равно|Возвращается значение|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>См. также:  
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-logical.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)  
  
  
