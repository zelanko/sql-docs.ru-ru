---
title: Оператор FREEZE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4738dab411fe55808034a6d9d81a16994089ea74
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68138290"
---
# <a name="mdx-scripting---freeze"></a>Сценарии многомерных выражений — FREEZE


  Фиксирует текущие значения ячеек заданного вложенного куба. Когда ячейки зафиксированы, изменения в других ячейках не влияют на них.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Аргументы  
 *Subcube_Expression*  
 Допустимое многомерное выражение, возвращающее вложенный куб.  
  
## <a name="remarks"></a>Remarks  
 Инструкция **Freeze** блокирует значения ячеек в указанном вложенном кубе, предотвращая изменение значений этих инструкций в СКРИПТе многомерных выражений при последующих проходах вычислений.  
  
 В следующем примере A и B представляют вложенные кубы в скрипте вычисления многомерного выражения:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 На данном этапе как A, так и B равно 3.  
  
 Теперь мы вставляем функцию **Freeze** для блокировки ячеек во вложенном кубе.  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 Теперь A равно 2, а B равно 3.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции для создания скриптов многомерных выражений (многомерные выражения)](../mdx/mdx-scripting-statements-mdx.md)  
  
  
