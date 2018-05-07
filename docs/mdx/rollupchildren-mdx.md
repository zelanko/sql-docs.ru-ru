---
title: RollupChildren (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ROLLUPCHILDREN
dev_langs:
- kbMDX
helpviewer_keywords:
- RollupChildren function
ms.assetid: 6f092540-067d-443f-b631-8523836a0d86
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 64c0bd0eca130d68fb57262fd30a20658e5b2742
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="rollupchildren-mdx"></a>RollupChildren (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает значение, сформированное сверткой значений дочерних элементов указанного элемента с помощью указанного унарного оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RollupChildren(Member_Expression, Unary_Operator)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Unary_Operator*  
 Допустимое строковое выражение, возвращающее унарный оператор.  
  
## <a name="remarks"></a>Замечания  
 **RollupChildren** функция сворачивает значения дочерних элементов указанного элемента, с помощью указанного унарного оператора.  
  
 В следующей таблице перечислены допустимые унарные операторы для этой функции.  
  
|Оператор|Результат|  
|--------------|------------|  
|**+**|сумма = сумма + текущий дочерний элемент|  
|**-**|сумма = сумма - текущий дочерний элемент|  
|**\***|сумма = сумма * текущий дочерний элемент|  
|**/**|сумма = сумма / текущий дочерний элемент|  
|**%**|сумма = (сумма / текущий дочерний элемент) * 100|  
|**~**|Дочерний элемент не участвует в свертке. Его значение не обрабатывается.|  
  
 Если в свойстве элемента указан оператор, которого нет в этом списке, возникает ошибка. Порядок вычисления определяется порядком элементов с общим родителем, а не старшинством операторов.  
  
## <a name="example"></a>Пример  
 В следующем примере для свертывания дочерних элементов иерархии Net Profit измерения Account применяется свойство элемента Alternate Rollup Operator, содержащее альтернативные значения для унарных операторов. Это свойство элемента отсутствует в кубе Adventure Works, но его можно создать. Такое использование **RollupChildren** можно использовать функцию приложения составления бюджета для гипотетического анализа.  
  
```  
RollupChildren  
   ( [Account].[Net Profit]  
   , [Account].CurrentMember.Properties ('Alternate Rollup Operator') )  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
