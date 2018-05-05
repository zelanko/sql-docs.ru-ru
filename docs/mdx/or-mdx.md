---
title: OR (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
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
- OR
dev_langs:
- kbMDX
helpviewer_keywords:
- OR operator
ms.assetid: 7634c08a-5b70-44cd-9422-6555fed6ae05
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6a9dddd834662871afa7fa08bb27ed9d4249628e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="or-mdx"></a>OR (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет логическое сложение двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>Параметры  
 Expression1  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
 Expression2  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, которое возвращает **true** Если один или оба аргумента принимают значение **true**; в противном случае **false**.  
  
## <a name="remarks"></a>Замечания  
 **Или** оператор рассматривает оба аргумента как логические значения (значение 0, как **false**; в противном случае **true**), прежде чем оператор выполнит логическое сложение. В следующей таблице показано, как **или** оператор выполнит логическое сложение.  
  
|*Expression1*|*Expression2*|Возвращаемое значение|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Пример  
 Приведенный ниже запрос содержит вычисляемую меру, возвращающую строку «MARRIED OR MALE», если текущий элемент иерархии Gender измерения Customer имеет значение Male либо текущий элемент иерархии Marital Status измерения Customer имеет значение Married. В противном случае возвращается строка «UNMARRIED OR FEMALE».  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
