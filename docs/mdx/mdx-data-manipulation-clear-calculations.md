---
title: Инструкция CLEAR CALCULATIONS (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CLEAR CALCULATIONS
- clalculations
- clear
dev_langs:
- kbMDX
helpviewer_keywords:
- clearing calculations
- CLEAR CALCULATIONS statement
- deleting calculations
- removing calculations
- calculations [Analysis Services], clearing
- cubes [Analysis Services], calculations
ms.assetid: aebec9a1-1d1d-4697-aa3f-cc2449625603
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ad7569a1db3d080c85dc0c45347c2dc011ee312d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Управление данными MDX - CLEAR CALCULATIONS
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Удаляет все вычисления из куба и возвращает куб к этапу вычисления 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Expression*  
 Допустимое многомерное выражение куба.  
  
## <a name="remarks"></a>Remarks  
 **FROM** предложение можно опустить, если контекст куба известен, например скрипт многомерных Выражений.  
  
> [!NOTE]  
>  Данная инструкция может быть выполнена только сервером, администратором базы данных или членом роли, имеющей доступ к исходным данным куба (то есть со свойством ReadSourceData=true).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции для манипулирования данными многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
