---
description: Определение данных многомерных выражений — DROP MEMBER
title: Инструкция DROP MEMBER (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f71232997c24a1bdca9a1294a804e8b30660d704
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483857"
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
  
## <a name="see-also"></a>См. также:  
 [Инструкция CREATE MEMBER &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-create-member.md)   
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
