---
title: '&lt;&gt; (Не равно) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac3241e7d6acd8ba883cdd59f9410f4a0fd9187d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63277518"
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt; (Не равно) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ)


  Выполняет операцию сравнения, определяющую, равно ли значение одного многомерного выражения значению другого многомерного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, определяемое исходя из следующих условий.  
  
-   **значение true,** Если оба аргумента не равны null и значение первого параметра не равно значению второго параметра.  
  
-   **false** Если оба аргумента не равны null и первый параметр равен значению второго параметра.  
  
-   Равно NULL, если любой из параметров или оба параметра возвращают значение NULL.  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
