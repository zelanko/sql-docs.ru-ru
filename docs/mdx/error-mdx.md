---
title: Ошибка (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6644318053321ae5189a70a2bd2c1f0e67d092fc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740713"
---
# <a name="error-mdx"></a>Error (многомерные выражения)


  Вызывает ошибку, при необходимости выводя заданное сообщение об ошибке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Текст_ошибки*  
 Допустимое строковое сообщение, содержащее сообщение об ошибке.  
  
## <a name="examples"></a>Примеры  
 Следующий запрос показывает использование **ошибка** функцию внутри вычисляемой меры:  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
