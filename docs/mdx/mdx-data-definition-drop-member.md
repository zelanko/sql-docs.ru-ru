---
title: Инструкция DROP MEMBER (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e8e38a3ff3f40f44c911a277f99ab9b629c7c87
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038193"
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
 [Инструкция CREATE MEMBER &#40;&#41;многомерных выражений](../mdx/mdx-data-definition-create-member.md)   
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
