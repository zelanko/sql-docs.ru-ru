---
title: Инструкция DROP MEMBER (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78d5d27853922d7e7524d93ae2b8157e57166968
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741383"
---
# <a name="mdx-data-definition---drop-member"></a>Определение данных MDX - удаления ЭЛЕМЕНТА


  Удаляет вычисляемый элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP MEMBER   
   CURRENTCUBE | Cube_Name  
      .Member_Name   
               [,CURRENTCUBE | Cube_Name.Member_Name ...n]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, представляющее имя куба.  
  
 *Member_Identifier*  
 Допустимое строковое выражение, представляющее имя или ключ элемента.  
  
## <a name="see-also"></a>См. также  
 [Инструкция CREATE MEMBER &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-create-member.md)   
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
