---
title: NOT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b4a28c6be2c956636f303ccc561936f799c63b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008251"
---
# <a name="not-dmx"></a>NOT (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Remarks  
 Аргумент логическим значением (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое отрицание. Если значение *expression1* равно true, оператор возвращает значение false. Если *expression1* имеет значение false, оператор возвращает значение true. В следующей таблице иллюстрируется выполнение логического умножения (конъюнкции).  
  
|Если Expression1 равно|Возвращается значение|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>См. также:  
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-logical.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)  
  
  
