---
title: "CustomData (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: EXISTS
dev_langs: kbMDX
helpviewer_keywords: Exists function
ms.assetid: 61d9f5a2-6f56-4179-a39b-317c8e0a2cdd
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: bab097e2a885745431dd3536162d8b7d905d6d61
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
