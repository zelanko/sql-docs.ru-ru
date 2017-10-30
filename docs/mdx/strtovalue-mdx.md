---
title: "StrToValue (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRTOVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToValue function
ms.assetid: 118a9c4f-74a3-48d5-a4f4-318664bc51bc
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9db77d7e3d4721337ccbeb397d6cb7382209f027
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="strtovalue-mdx"></a>StrToValue (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает числовое значение, заданное форматированной строкой многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *MDX_Expression*  
 Допустимое строковое выражение, разрешающееся (напрямую или косвенно) в одну ячейку.  
  
## <a name="remarks"></a>Замечания  
 **StrToValue** функция возвращает числовое значение, заданное Многомерным выражением. **StrToValue** функция обычно используется с пользовательскими функциями для передачи Многомерного выражения из внешней функции обратно в инструкцию многомерных Выражений, которое разрешается в одну ячейку.  
  
-   При использовании флага CONSTRAINED многомерное выражение должно содержать только скалярное значение. Флаг CONSTRAINED позволяет снизить вероятность атак через указанную строку. Если указано Многомерное выражение, которое не разрешается до скалярной величины, возникает следующая ошибка: «ограничения, установленные флагом CONSTRAINED функции STRTOVALUE нарушены.»  
  
-   Без флага CONSTRAINED можно использовать многомерные выражения любой сложности, если они разрешаются в допустимое многомерной выражение, возвращающее одну ячейку.  
  
> [!NOTE]  
>  Возвращение результата многомерного выражения в виде числового значения полезно использовать, если значение хранится в текстовом виде и требуется выполнить арифметические операции над возвращаемыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **StrToValue** функции возвращается вес каждого велосипеда.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

