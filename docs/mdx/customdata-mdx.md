---
description: CustomData (многомерные выражения)
title: CustomData (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ed7bfe2841caf9bd5b2c6e6caf102323db6d62ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413170"
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
