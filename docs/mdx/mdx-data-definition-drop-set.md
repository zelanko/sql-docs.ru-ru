---
description: Определение данных многомерных выражений — DROP SET
title: Инструкция DROP SET (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5c4ca356847d75150aa098b331bdf0f8c8368bb6
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195609"
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
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения об именованных наборах см. в разделе [Построение именованных наборов в многомерных выражениях](/analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
