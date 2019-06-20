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
manager: kfile
ms.openlocfilehash: 3b70068562ff24e8a1619b85fe091ab3e17da173
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63278496"
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
  
  
