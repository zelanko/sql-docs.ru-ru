---
title: NOT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 98c40dba282c82f124d4e4ac009a046a44a283cb
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971639"
---
# <a name="not-dmx"></a>NOT (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Логический оператор, выполняющий логическое отрицание числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение возвращает значение FALSE, если аргумент возвращает значение TRUE, и TRUE в противном случае.  
  
## <a name="remarks"></a>Комментарии  
 Аргумент логическим значением (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое отрицание. Если значение *expression1* равно true, оператор возвращает значение false. Если *expression1* имеет значение false, оператор возвращает значение true. В следующей таблице иллюстрируется выполнение логического умножения (конъюнкции).  
  
|Если Expression1 равно|Возвращается значение|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>См. также  
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-logical.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)  
  
  
