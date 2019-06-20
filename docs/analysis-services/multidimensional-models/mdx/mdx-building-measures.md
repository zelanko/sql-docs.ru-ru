---
title: Построение мер в многомерных Выражениях | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c2095d3bde254a59c5b2edbe8ebb117854ab7777
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62806138"
---
# <a name="mdx-building-measures"></a>Меры построения многомерных выражений
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Инструкция CREATE MEMBER (многомерные выражения)](../../../mdx/mdx-data-definition-create-member.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../../../mdx/mdx-function-reference-mdx.md)   
 [Инструкция SELECT (многомерные выражения)](../../../mdx/mdx-data-manipulation-select.md)  
  
  
