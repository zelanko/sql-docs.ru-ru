---
title: Операторы (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea7e6c9b8acb3301174a1e4086aee3844eb1ee81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174514"
---
# <a name="operators-ssis-expression"></a>Операторы (выражение служб SSIS)
  В этом разделе дано описание операторов, возможность использования которых дает язык выражений, а также их приоритет и ассоциативность, используемую средством оценки выражений.  
  
 В следующей таблице содержится список разделов, посвященных операторам.  
  
|Оператор|Описание|  
|--------------|-----------------|  
|[Приведение &#40;выражение служб SSIS&#41;](cast-ssis-expression.md)|Преобразует выражение одного типа данных в другой тип данных.|  
|[&#40;&#41;&#40;Скобки&#41; &#40;выражение служб SSIS&#41;](parentheses-ssis-expression.md)|Определяет порядок вычисления выражений.|  
|[+ &#40;Добавить&#41; &#40;служб SSIS&#41;](add-ssis.md)|Складывает два числовых выражения.|  
|[+ &#40;СЦЕПИТЬ&#41; &#40;выражение служб SSIS&#41;](concatenate-ssis-expression.md)|Сцепляет два выражения.|  
|[- &#40;Вычесть&#41; &#40;выражение служб SSIS&#41;](subtract-ssis-expression.md)|Вычитает второе числовое выражение из первого.|  
|[- &#40;Negate&#41; &#40;выражение служб SSIS&#41;](negate-ssis-expression.md)|Инвертирует числовое выражение.|  
|[&#42;&#40;Умножение&#41; &#40;выражение служб SSIS&#41;](multiply-ssis-expression.md)|Умножает два числовых выражения.|  
|[Разделить &#40;выражение служб SSIS&#41;](divide-ssis-expression.md)|Делит первое числовое выражение на второе.|  
|[&#40;Остаток от деления&#41; &#40;выражение служб SSIS&#41;](modulo-ssis-expression.md)|Вычисляет целочисленный остаток после деления первого числового выражения на второе.|  
|[&#124;&#124;&#40;Логическое или&#41; &#40;выражение служб SSIS&#41;](logical-or-ssis-expression.md)|Выполняет логическую операцию ИЛИ.|  
|[& & &#40;Логическое и&#41; &#40;выражение служб SSIS&#41;](logical-and-ssis-expression.md)|Выполняет логическую операцию И.|  
|[! &#40;Логическое не&#41; &#40;выражение служб SSIS&#41;](logical-not-ssis-expression.md)|Инвертирует логический операнд.|  
|[&#124;&#40;Побитовое включающее или&#41; &#40;выражение служб SSIS&#41;](bitwise-inclusive-or-ssis-expression.md)|Выполняет побитовую операцию ИЛИ для двух целочисленных значений.|  
|[^ &#40;Побитовое исключающее или&#41; &#40;выражение служб SSIS&#41;](bitwise-exclusive-or-ssis-expression.md)|Выполняет побитовую исключающую операцию ИЛИ для двух целочисленных значений.|  
|[& &#40;Побитовое и&#41; &#40;выражение служб SSIS&#41;](bitwise-and-ssis-expression.md)|Выполняет побитовую операцию И для двух целочисленных значений.|  
|[~ &#40;Побитовое не&#41; &#40;выражение служб SSIS&#41;](bitwise-not-ssis-expression.md)|Выполняет битовую инверсию целого числа.|  
|[== &#40;Равно&#41; &#40;выражение служб SSIS&#41;](equal-ssis-expression.md)|Выполняет сравнение с целью определения равенства двух выражений.|  
|[\!= (не равно) (выражение служб SSIS)](unequal-ssis-expression.md)|Осуществляет операцию сравнения для определения неравенства двух выражений.|  
|[&#62;&#40;Больше, чем&#41; &#40;выражение служб SSIS&#41;](greater-than-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение больше второго.|  
|[&#60;&#40;Меньше, чем&#41; &#40;выражение служб SSIS&#41;](less-than-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение меньше второго.|  
|[&#62;= &#40;Больше или равно&#41; &#40;выражение служб SSIS&#41;](greater-than-or-equal-to-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение больше второго или равно ему.|  
|[&#60;= &#40;Меньше или равно&#41; &#40;выражение служб SSIS&#41;](less-than-or-equal-to-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение меньше второго или равно ему.|  
|[? : (условный) (выражение служб SSIS)](conditional-ssis-expression.md)|Возвращает одно из двух выражений на основе вычисления логического выражения.|  
  
 Сведения о размещении каждого оператора в иерархии приоритета см. в разделе [Operator Precedence and Associativity](operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)   
 [Примеры расширенных выражений служб Integration Services](examples-of-advanced-integration-services-expressions.md)   
 [Выражения служб Integration Services (SSIS)](integration-services-ssis-expressions.md)  
  
  
