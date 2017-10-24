---
title: "Арифметические выражения (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6ba5c642195f1049f7df59a0fa14ef666eec4bfe
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="arithmetic-expressions-xquery"></a>Арифметические выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Поддерживаются все арифметические операторы, за исключением **idiv**. Следующие примеры иллюстрируют использование арифметических операторов:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Поскольку **idiv** — не поддерживается, решение заключается в использовании **xs:integer()** конструктор:  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Тип результата арифметического оператора зависит от типов входных значений. Если операнды имеют различные типы, то при необходимости они будут приведены к общему базовому типу в соответствии с иерархией типов. Сведения об иерархии типов см. в разделе [правила приведения типов в языке XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 Если обе операции имеют различные числовые базовые типы, то проводится преобразование типов. Например, при добавлении **xs: decimal** для **xs: double** , сначала производится десятичного значения к типу double. Затем выполняется операция сложения, в результате которой получается значение типа double.  
  
 Нетипизированные элементарные значения приводятся к базовому числовому типу второго операнда, а также к **xs: double** Если значение второго операнда не типизированы.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Аргументы арифметических операторов должны иметь числовой тип или **untypedAtomic**.  
  
-   Операции с **xs: Integer** значения в результате значение типа **xs: decimal** вместо **xs: Integer**.  
  
  

