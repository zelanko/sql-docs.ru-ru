---
title: Инструкция FREEZE (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cd652a9f308bd7a564a61d165f9c47875a900737
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187565"
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
  
## <a name="remarks"></a>Примечания  
 **ЗАМОРОЗИТЬ** инструкция блокирует значения ячеек в указанный вложенный куб, предотвращая последующие инструкции многомерных выражений передает сценарий изменение их значений в последующих вычислений.  
  
 В следующем примере A и B представляют вложенные кубы в скрипте вычисления многомерного выражения:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 На данном этапе как A, так и B равно 3.  
  
 Теперь вставьте **заморозить** функция блокировки ячейки вложенного куба:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 Теперь A равно 2, а B равно 3.  
  
## <a name="see-also"></a>См. также  
 [Инструкции для создания скриптов многомерных выражений (многомерные выражения)](../mdx/mdx-scripting-statements-mdx.md)  
  
  
