---
title: Построение мер в многомерных Выражениях | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7587e3304d1464beb7ef94cd7d3093982f394bcc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074589"
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
 [Инструкция CREATE MEMBER (многомерные выражения)](/sql/mdx/mdx-data-definition-create-member)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](/sql/mdx/mdx-function-reference-mdx)   
 [Инструкция SELECT (многомерные выражения)](/sql/mdx/mdx-data-manipulation-select)  
  
  
