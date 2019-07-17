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
ms.openlocfilehash: 165d03b886ad8e9beeb09bf5a835c879cc23a2a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055583"
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
  
  
