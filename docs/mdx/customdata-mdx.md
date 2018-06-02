---
title: CustomData (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5161bb180b6acdf8f6ab6d16d6d0f15bd8f40a39
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577816"
---
# <a name="customdata-mdx"></a>CustomData (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает значение **CustomData** свойство строки подключения, если определен; в противном случае — **null**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **CustomData** может получить функция **CustomData** свойства строки соединения и передавать параметр конфигурации для использоваться функции многомерных выражений (MDX) и инструкции, такие как [UserName (многомерные Выражения)](../mdx/username-mdx.md) и [инструкция CALL (Многомерные)](../mdx/mdx-data-manipulation-call.md). Например, эта функция может использоваться в динамическом выражении безопасности для выбора разрешенных или запрещенных наборов элементов для строкового значения в **CustomData** свойство строки соединения.  
  
## <a name="example"></a>Пример  
 Следующий запрос отображает значение, возвращаемое **CustomData** функции в вычисляемой мере:  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
