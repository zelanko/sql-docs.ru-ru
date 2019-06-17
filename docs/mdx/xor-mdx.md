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
manager: kfile
ms.openlocfilehash: f9115fc1e226e05c788206706d59a5435bfd1c5d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251490"
---
# <a name="xor-mdx"></a>XOR (многомерные выражения)


  Выполняет логическое исключение над двумя числовыми выражениями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, возвращающее **true** Если один и только один аргумент принимает значение **true**; в противном случае **false**.  
  
## <a name="remarks"></a>Примечания  
 **XOR** оператор рассматривает оба аргумента как логические (значение 0, соответствует **false**; в противном случае **true**) прежде, чем оператор выполнит логическое исключение. В следующей таблице показано как **XOR** оператор выполнит логическое исключение.  
  
|*Expression1*|*Expression2*|Возвращаемое значение|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
