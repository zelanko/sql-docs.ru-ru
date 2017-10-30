---
title: "&lt;&gt;(Не равно) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- <>
dev_langs:
- kbMDX
helpviewer_keywords:
- not equal to operator (<>)
- <> (not equal to operator)
ms.assetid: b4eb3f1c-8b68-4530-a8f3-e3b8414ac789
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 94a88e2b78f577fb09396851668fcf72c7148d0e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt;(Не равно) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
-   **false** Если оба аргумента не равны null и значение первого параметра равно значению второго параметра.  
  
-   Равно NULL, если любой из параметров или оба параметра возвращают значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

