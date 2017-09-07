---
title: "Predict (многомерные Выражения) | Документы Microsoft"
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
- PREDICT
dev_langs:
- kbMDX
helpviewer_keywords:
- Predict function
ms.assetid: a82f3edd-249b-4559-98d3-6e10d81a095d
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7bec1c96bd70b9b75c3a8c212cf1f6c04c27c73e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="predict-mdx"></a>Predict (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
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
  
  

