---
description: Members (строка) (многомерные выражения)
title: Members (String) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 95e90f488f4b9182fc237045b570bc9da02f47e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483827"
---
# <a name="members-string-mdx"></a>Members (строка) (многомерные выражения)


  Возвращает элемент, заданный строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, обозначающее имя элемента.  
  
## <a name="remarks"></a>Remarks  
 Функция **Members (String)** возвращает единственный элемент, имя которого указано. Как правило, функция **Members (String)** используется с внешними функциями, предоставляя функции **Members (String)** строку, определяющую элемент, а функция **Members (String)** возвращает значение для этого указанного элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере используется функция **Members (String)** для преобразования указанной строки в допустимый элемент, а затем возвращается мера по умолчанию для элемента, указанного в строке. Указанная строка приведена в одинарных кавычках. Мерой по умолчанию является Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
