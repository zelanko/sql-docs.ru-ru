---
title: НЕ (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4031b887eb0a42580d6ae8debf6c9177ff67efc3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
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
 Логическое значение, возвращающее **false** Если аргумент принимает значение **true**; в противном случае **true**.  
  
## <a name="remarks"></a>Примечания  
 **Не** оператор рассматривает выражение как логическое значение (значение 0, соответствует **false**; в противном случае **true**) прежде, чем оператор выполнит логическое отрицание. В следующей таблице показано как **не** оператор выполнит логическое отрицание.  
  
|*Expression1*|Возвращаемое значение|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
