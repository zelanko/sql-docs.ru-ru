---
title: "Predict (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: PREDICT
dev_langs: kbMDX
helpviewer_keywords: Predict function
ms.assetid: a82f3edd-249b-4559-98d3-6e10d81a095d
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: feeadc92c9b30013f3e45e54a7b6464cf0743442
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="predict-mdx"></a>Predict (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

    
> [!CAUTION]  
>  Эта функция находится в процессе удаления из-за внутренних несогласованностей.  
>   
>  Решение этой проблемы с помощью выражения расширений интеллектуального анализа данных приведено в разделе примеров.  
  
 Возвращает значение числового выражения, вычисленного по модели интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Mining_Model_Name*  
 Допустимое строковое выражение, представляющее собой модель интеллектуального анализа данных.  
  
 *String_Expression*  
 Допустимое строковое выражение, результатом которого является допустимое выражение DMX для указанной модели интеллектуального анализа данных.  
  
## <a name="remarks"></a>Замечания  
 **Predict** функция вычисляет указанного строкового выражения в контексте заданную модель анализа.  
  
 Синтаксис и функции интеллектуального анализа данных описаны в справочнике по выражениям интеллектуального анализа данных.  
  
## <a name="example"></a>Пример  
 Приведенный ниже пример прогнозирует имя кластера и расстояние от него до конкретного клиента с помощью модели интеллектуального анализа данных Customer Clusters:  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
