---
title: "Построение мер в многомерных Выражениях | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5d1e4e637d3cee754573c2d59776d7241c89d2bf
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-building-measures"></a>Построение многомерного Выражения мер
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]В многомерных выражениях (MDX), мера — это именованное выражение DAX, которое разрешается путем вычисления и возвращают значение в табличной модели. В этом определении кроется огромный потенциал. Создание и использование мер в многомерных запросах дает широкие возможности для табличных данных.  
  
> [!WARNING]  
>  Меры могут быть определены только в табличных моделях. Если база данных работает в режиме многомерных выражений, создание мер будет формировать ошибку.  
  
 Чтобы создать меру, которая определена как часть запроса многомерных выражений, с областью, ограниченной этим запросом, используется ключевое слово WITH. Затем меру можно использовать внутри инструкции MDX SELECT. Этот подход позволяет изменять вычисляемый элемент, созданный при помощи ключевого слова WITH, не изменяя инструкцию SELECT. Однако в многомерных выражениях ссылаться на меру нужно не так, как в DAX-выражениях; для ссылки на эту меру ее нужно рассматривать как элемент измерения [Measures], как в следующем примере с использованием многомерных выражений:  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 Возвращает следующие данные при выполнении:  
  
||Total Sales Amount||  
|-|------------------------|-|  
|2001|11331808.96||  
|2002|30674773.18||  
|2003|41993729.72||  
|2004|25808962.34||  
  
## <a name="see-also"></a>См. также  
 [Инструкция CREATE MEMBER (многомерные выражения)](../../../mdx/mdx-data-definition-create-member.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../../../mdx/mdx-function-reference-mdx.md)   
 [Инструкция SELECT &#40; Многомерные Выражения &#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  
