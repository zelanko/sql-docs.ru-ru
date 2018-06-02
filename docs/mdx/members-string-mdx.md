---
title: Members (строка) (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 36d5d3a8573346d164c77881ff80b17feacf8191
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580516"
---
# <a name="members-string-mdx"></a>Members (строка) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элемент, заданный строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, обозначающее имя элемента.  
  
## <a name="remarks"></a>Примечания  
 **Members (строка)** функция возвращает единственный элемент с заданным именем. Обычно используется **Members (строка)** функция с внешними функциями, предоставление **Members (строка)** строка, определяющая член, функции и **Members (строка)** функция возвращает значение для указанного элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **Members (строка)** для преобразования заданной строки является допустимый элемент и затем возвращается мера по умолчанию для элемента, указанного в строке. Указанная строка приведена в одинарных кавычках. Мерой по умолчанию является Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
