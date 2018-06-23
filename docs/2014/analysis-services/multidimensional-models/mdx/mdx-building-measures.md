---
title: Построение мер в многомерных Выражениях | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 62781abfc548ad890719fc5b6dfcbf19b0e05f5a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101863"
---
# <a name="building-measures-in-mdx"></a>Построение мер в многомерных выражениях
  В многомерных выражениях мера — это именованное DAX-выражение, которое разрешается путем вычисления и возвращает значение в табличную модель. В этом определении кроется огромный потенциал. Создание и использование мер в многомерных запросах дает широкие возможности для табличных данных.  
  
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
 [Инструкция CREATE MEMBER &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [Инструкция SELECT &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
