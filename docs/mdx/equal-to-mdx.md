---
title: "= (Равно) (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: =
dev_langs: kbMDX
helpviewer_keywords:
- equals operator (=)
- = (equals operator)
ms.assetid: 5e1f3b58-a646-4fc1-a3f1-19090a5437b7
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 51df250577d539c48acb55e26e9906cf1d5a15d4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="-equal-to-mdx"></a>= (равно) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет операцию сравнения, определяющую, равно ли значение одного многомерного выражения значению другого многомерного выражения.  
  
> [!NOTE]  
>  Для сравнения объектов используйте [IS &#40; Многомерные Выражения &#41; ](../mdx/is-mdx.md) оператор. Например, используйте оператор IS для проверки, является ли текущий элемент на оси запросов конкретным элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MDX_Expression = MDX_Expression   
```  
  
#### <a name="parameters"></a>Параметры  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, определяемое исходя из следующих условий.  
  
-   **значение true,** Если значение первого параметра равно значению второго параметра.  
  
-   **false** Если значение первого параметра не равно значению второго параметра.  
  
-   **значение true,** Если оба параметра имеют значение null, или один параметр имеет значение null и других параметров — 0.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показаны примеры этих условий:  
  
 `With`  
  
 `--Returns true`  
  
 `Member [Measures].bool1 as 1=1`  
  
 `--Returns false`  
  
 `Member [Measures].bool2 as 1=0`  
  
 `--Returns true`  
  
 `Member [Measures].bool3 as null=null`  
  
 `--Returns true`  
  
 `Member [Measures].bool4 as 0=null`  
  
 `--Returns false`  
  
 `Member [Measures].bool5 as 1=null`  
  
 `Select {[Measures].bool1,[Measures].bool2,[Measures].bool3,[Measures].bool4,[Measures].bool5}`  
  
 `On 0`  
  
 `From [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
