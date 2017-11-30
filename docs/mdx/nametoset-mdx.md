---
title: "NameToSet (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: NAMETOSET
dev_langs: kbMDX
helpviewer_keywords: NameToSet function
ms.assetid: e02e17d5-4309-49cb-84c7-5b445ac2bd94
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: adf905695fd42a64f4f4705222fcf52f624f509a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="nametoset-mdx"></a>NameToSet (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор, содержащий элементы, заданные форматированной строкой многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, представляющее собой имя элемента.  
  
## <a name="remarks"></a>Замечания  
 Если указанное имя элемента существует, **NameToSet** функция возвращает набор, содержащий данный элемент. В противном случае функция возвращает пустой набор.  
  
> [!NOTE]  
>  Заданное имя элемента должно быть только именем элемента, оно не может быть выражением элемента. Чтобы использовать выражение элемента, см. [StrToSet &#40; Многомерные Выражения &#41; ](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение меры по умолчанию для заданного имени элемента.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
