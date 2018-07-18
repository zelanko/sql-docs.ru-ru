---
title: Инструкция CLEAR CALCULATIONS (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cdc4b2d3e948f0123eb15e38a6140e63009907bc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742393"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Управление данными MDX - CLEAR CALCULATIONS


  Удаляет все вычисления из куба и возвращает куб к этапу вычисления 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Expression*  
 Допустимое многомерное выражение куба.  
  
## <a name="remarks"></a>Примечания  
 **FROM** предложение можно опустить, если контекст куба известен, например скрипт многомерных Выражений.  
  
> [!NOTE]  
>  Данная инструкция может быть выполнена только сервером, администратором базы данных или членом роли, имеющей доступ к исходным данным куба (то есть со свойством ReadSourceData=true).  
  
## <a name="see-also"></a>См. также  
 [Инструкции языка манипулирования данными &#40;многомерных Выражений&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
