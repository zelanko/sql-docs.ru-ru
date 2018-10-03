---
title: Арифметические выражения (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3d970209b71a842aa1c78b2f7dd0db980e0ce73e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642652"
---
# <a name="arithmetic-expressions-xquery"></a>Арифметические выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Поддерживаются все арифметические операторы, за исключением **idiv**. Следующие примеры иллюстрируют использование арифметических операторов:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Так как **idiv** — не поддерживается, решение заключается в использовании **xs:integer()** конструктор:  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Тип результата арифметического оператора зависит от типов входных значений. Если операнды имеют различные типы, то при необходимости они будут приведены к общему базовому типу в соответствии с иерархией типов. Сведения об иерархии типов см. в разделе [правила приведения типов в XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 Если обе операции имеют различные числовые базовые типы, то проводится преобразование типов. Например, добавление **xs: decimal** для **xs: double** сначала следует изменить десятичное значение к типу double. Затем выполняется операция сложения, в результате которой получается значение типа double.  
  
 Нетипизированные элементарные значения приводятся к базовому числовому типу второго операнда или **xs: double** Если значение второго операнда не типизированы.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Аргументы арифметических операторов должны иметь числовой тип или **untypedAtomic**.  
  
-   Операции с **xs: Integer** значения привести к значению типа **xs: decimal** вместо **xs: Integer**.  
  
  
