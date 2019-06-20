---
title: Members (строка) (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 302445cadc829de35eca28db2888aaa01673ca75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048457"
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
  
## <a name="remarks"></a>Примечания  
 **Members (строка)** функция возвращает единственный элемент с заданным именем. Как правило, используется **Members (строка)** функции с внешними функциями, предоставляя **Members (строка)** функции строка, определяющая член, и **Members (строка)**  функция возвращает значение для указанного элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере используется **Members (строка)** преобразовать указанную строку в допустимый элемент и затем возвращает меру по умолчанию для элемента, указанного в строке. Указанная строка приведена в одинарных кавычках. Мерой по умолчанию является Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
