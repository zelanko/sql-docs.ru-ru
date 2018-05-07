---
title: Members (строка) (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Members
dev_langs:
- kbMDX
helpviewer_keywords:
- Members function
ms.assetid: 21fca354-448b-4b05-93f4-111bde1568f1
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 22e50f54105fdba6fe49f346a44f53246109002c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 **Members (строка)** функция возвращает единственный элемент с заданным именем. Обычно используется **Members (строка)** функция с внешними функциями, предоставление **Members (строка)** строка, определяющая член, функции и **Members (строка)** функция возвращает значение для указанного элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **Members (строка)** для преобразования заданной строки является допустимый элемент и затем возвращается мера по умолчанию для элемента, указанного в строке. Указанная строка приведена в одинарных кавычках. Мерой по умолчанию является Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
