---
title: Инструкция DROP MEMBER (многомерные Выражения) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248303"
---
# <a name="mdx-data-definition---drop-member"></a>Определение данных многомерных выражений — DROP MEMBER


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
 [Инструкция CREATE MEMBER (многомерные выражения)](../mdx/mdx-data-definition-create-member.md)   
 [Инструкции определения данных многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
