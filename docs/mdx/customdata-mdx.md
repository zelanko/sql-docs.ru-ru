---
title: CustomData (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d2884e23cbee78acacdb72e386f0e99610e9629f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135828"
---
# <a name="customdata-mdx"></a>CustomData (многомерные выражения)


  Возвращает значение свойства строки подключения **CustomData** , если оно определено. в противном случае **значение NULL**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Функция **CustomData** может извлекать свойство строки подключения **CustomData** и передавать параметр конфигурации для использования в функциях и инструкциях многомерных выражений, таких как [username (многомерные выражения)](../mdx/username-mdx.md) и [инструкция Call (многомерные выражения)](../mdx/mdx-data-manipulation-call.md). Например, эта функция может использоваться в динамическом выражении безопасности для выбора разрешенных и запрещенных элементов Set для строкового значения в свойстве строки соединения **CustomData** .  
  
## <a name="example"></a>Пример  
 Следующий запрос отображает значение, возвращаемое функцией **CustomData** в вычисляемой мере:  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
