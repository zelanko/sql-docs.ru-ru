---
title: Инструкция CLEAR для вычислений (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b0766cb002960a96d702184ac9719abe7610afd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938023"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Операции с данными многомерных выражений — CLEAR CALCULATIONS


  Удаляет все вычисления из куба и возвращает куб к этапу вычисления 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Expression*  
 Допустимое многомерное выражение куба.  
  
## <a name="remarks"></a>Remarks  
 Предложение **from** можно опустить, если известен контекст куба, например в СКРИПТе многомерных выражений.  
  
> [!NOTE]  
>  Данная инструкция может быть выполнена только сервером, администратором базы данных или членом роли, имеющей доступ к исходным данным куба (то есть со свойством ReadSourceData=true).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции обработки данных многомерных выражений &#40;многомерные выражения&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
