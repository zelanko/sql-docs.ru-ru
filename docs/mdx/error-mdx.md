---
title: "Ошибка (многомерные Выражения) | Документы Microsoft"
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
- ERROR
dev_langs:
- kbMDX
helpviewer_keywords:
- Error function
ms.assetid: 2caac19b-b297-443e-9299-648ef88a5039
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b439b8b6d6c36cf500ad5f089a24034e7d2404fb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="error-mdx"></a>Error (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

