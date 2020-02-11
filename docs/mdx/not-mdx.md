---
title: NOT (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4031b887eb0a42580d6ae8debf6c9177ff67efc3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088228"
---
# <a name="not-mdx"></a>NOT (многомерные выражения)


  Выполняет операцию логического отрицания над числовым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, которое возвращает значение **false** , если аргумент принимает **значение true**; в противном случае — **значение true**.  
  
## <a name="remarks"></a>Remarks  
 Оператор **Not** обрабатывает выражение как логическое значение (ноль, 0, как **false**; в противном случае — **значение true**), прежде чем оператор выполняет логическое отрицание. В следующей таблице показано, как оператор **Not** выполняет логическое отрицание.  
  
|*Expression1*|Возвращаемое значение|  
|-------------------|------------------|  
|**условия**|**IsFalse**|  
|**IsFalse**|**условия**|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)  
  
  
