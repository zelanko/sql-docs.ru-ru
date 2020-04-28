---
title: XOR (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1657d9e58a0ae729a67e179602cd9a886ae923b1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125793"
---
# <a name="xor-mdx"></a>XOR (многомерные выражения)


  Выполняет логическое исключение над двумя числовыми выражениями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>Параметры  
 *Выражения*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, возвращающее **значение true** , если один и только один аргумент имеет **значение true**; в противном случае — **значение false**.  
  
## <a name="remarks"></a>Remarks  
 Оператор **XOR** обрабатывает оба параметра как логические значения (ноль, 0, как **false**; в противном случае — **значение true**), прежде чем оператор выполняет логическое исключение. В следующей таблице показано, как оператор **XOR** выполняет логическое исключение.  
  
|*Выражения*|*Expression2*|Возвращаемое значение|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)  
  
  
