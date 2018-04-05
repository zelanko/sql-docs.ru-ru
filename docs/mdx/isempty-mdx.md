---
title: IsEmpty (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ISEMPTY
dev_langs:
- kbMDX
helpviewer_keywords:
- IsEmpty function
ms.assetid: b4a50996-61d1-4e23-8003-7d530195ea72
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 6f6d53545c505b32f9c9d045f07260cb23514641
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="isempty-mdx"></a>IsEmpty (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает значение, сообщающее, является ли вычисленное выражение значением пустой ячейки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Value_Expression*  
 Допустимое многомерное выражение, обычно возвращающее координаты ячейки элемента или кортежа.  
  
## <a name="remarks"></a>Remarks  
 **IsEmpty** возврата функцией **true** Если вычисленное выражение принимает значение пустой ячейки. В противном случае эта функция возвращает **false**.  
  
> [!NOTE]  
>  Свойство элемента по умолчанию — значение элемента.  
  
 **IsEmpty** функция это единственный способ надежно проверки пустую ячейку, так как значение пустой ячейки имеет особый смысл в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!IMPORTANT]  
>  При вычислении значения выражения возвращает ошибку, то функция вернет **false**. Значение выражения возвращает ошибку, например, в том случае, если ссылка свойств указывает на недопустимое или несуществующее свойство.  
  
 Дополнительные сведения о пустых ячейках см. в документации по OLE DB.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение TRUE, если мера Internet Sales Amount для текущего элемента иерархии Fiscal в измерении Date возвращает пустую ячейку:  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Работа с пустыми значениями](../mdx/working-with-empty-values.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
