---
title: Unorder (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 954a71c8ca2e96d905892d77ff12b7270deded5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
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
  
## <a name="remarks"></a>Примечания  
 **Unorder** функция удаляет упорядочение кортежей в наборе с любой другой функцией или инструкцией, такие как [порядок](../mdx/order-mdx.md) функции. Порядок кортежей в наборе, возвращаемом **Unorder** функции не определен.  
  
 **Unorder** функция используется в качестве подсказки для для оптимизации запросов для обработки набора. Если порядок кортежей в наборе не важен для вычислений запроса, с помощью **Unorder** функции может улучшить производительность в таких случаях. Например [NonEmpty (многомерные Выражения)](../mdx/nonempty-mdx.md) функция может выполняться лучше, если предоставленный набор для этой функции неупорядочен, чем если [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] приходится сохранять порядок, хотя с [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], обработчик запросов пытается выполнить Эта функция автоматически для многих функций, таких как **Sum** и **агрегатные**. Преимущества высокой производительности с помощью **Unorder** вероятнее всего, только быть заметной с очень большими наборами, состоящими из миллионов кортежей.  
  
## <a name="example"></a>Пример  
 Следующий псевдокод иллюстрирует синтаксис для этой функции.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
