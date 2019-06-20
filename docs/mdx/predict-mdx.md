---
title: Predict (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca47db953df9889cb1d72d0add45f2b0ed681980
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63277475"
---
# <a name="predict-mdx"></a>Predict (многомерные выражения)


    
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
  
## <a name="remarks"></a>Примечания  
 **Predict** функция вычисляет указанного строкового выражения в контексте указанной модели.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
