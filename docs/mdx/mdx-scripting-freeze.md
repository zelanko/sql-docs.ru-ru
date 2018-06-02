---
title: Инструкция FREEZE (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b7eb3a3939ce8525dc57d27a24ac005ecb2cf2d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579906"
---
# <a name="mdx-scripting---freeze"></a>Сценарии многомерных Выражений - ЗАКРЕПЛЕНИЯ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Фиксирует текущие значения ячеек заданного вложенного куба. Когда ячейки зафиксированы, изменения в других ячейках не влияют на них.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Аргументы  
 *Subcube_Expression*  
 Допустимое многомерное выражение, возвращающее вложенный куб.  
  
## <a name="remarks"></a>Примечания  
 **ЗАКРЕПИТЬ** инструкции фиксирует значения ячеек заданного вложенного куба, предотвращает последующие инструкции многомерных выражений передает сценарий изменять их значения в последующих вычислений.  
  
 В следующем примере A и B представляют вложенные кубы в скрипте вычисления многомерного выражения:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 На данном этапе как A, так и B равно 3.  
  
 Теперь введите **закрепить** функция заблокировать ячейки вложенного куба:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 Теперь A равно 2, а B равно 3.  
  
## <a name="see-also"></a>См. также  
 [Инструкции сценариев многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
