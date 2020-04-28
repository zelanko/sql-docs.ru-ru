---
title: Unorder (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 954a71c8ca2e96d905892d77ff12b7270deded5f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097259"
---
# <a name="unorder-mdx"></a>Unorder (многомерные выражения)


  Удаляет принудительное упорядочивание заданного набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 Функция **Unorder** удаляет порядок, накладываемый на кортежи, содержащиеся в наборе любыми другими функциями или операторами, такими как функция [Order](../mdx/order-mdx.md) . Порядок кортежей в наборе, возвращаемом функцией **Unorder** , является неопределенным.  
  
 Функция **Unorder** используется в качестве подсказки для оптимизации запросов для обработки набора. Если порядок кортежей в наборе не важен для вычисления или запроса, использование функции **Unimportant** может обеспечить выигрыш в производительности в таких случаях. Например, функция [непустых (многомерных выражений)](../mdx/nonempty-mdx.md) может работать лучше, если в наборе, предоставленном этой функции, не [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] упорядочен, чем при необходимости сохранения порядка [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], хотя обработчик запросов пытается автоматически выполнить эту функцию для многих функций, таких как **Sum** и **Aggregate**. Преимущество в производительности в случае **неупорядоченности** , скорее всего, будет заметным только для очень больших наборов, состоящих из миллионов кортежей.  
  
## <a name="example"></a>Пример  
 Следующий псевдокод иллюстрирует синтаксис для этой функции.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
