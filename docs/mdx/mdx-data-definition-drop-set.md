---
title: Инструкция DROP SET (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f4e31a687597e454b9afe38d6c6dd1c15af486d0
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893724"
---
# <a name="mdx-data-definition---drop-set"></a>Определение данных многомерных выражений — DROP SET


  Удаляет именованный набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP [SESSION] SET   
   <Cube_Reference>.Set_Name   
               [,<Cube_Reference>.Set_Name ...n]  
  
<Cube_Reference> ::= {CURRENTCUBE | Cube_Name}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, представляющее имя куба.  
  
 *Set_Name*  
 Допустимое строковое выражение, представляющая имя именованного набора для удаления.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets).  
  
## <a name="see-also"></a>См. также  
 [Многомерные выражения инструкций &#40;определения данных многомерных выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
