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
ms.openlocfilehash: cbceb75a036343b0d116481c5e36e3da3aa63a85
ms.sourcegitcommit: 87fec38a515a7c524b7c99f99bc6f4d338e09846
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2018
ms.locfileid: "51272592"
---
# <a name="operators-ssis-expression"></a>Операторы (выражение служб SSIS)
  В этом разделе дано описание операторов, возможность использования которых дает язык выражений, а также их приоритет и ассоциативность, используемую средством оценки выражений.  
  
 В следующей таблице содержится список разделов, посвященных операторам.  
  
|Оператор|Описание|  
|--------------|-----------------|  
|[Приведение (выражение служб SSIS)](cast-ssis-expression.md)|Преобразует выражение одного типа данных в другой тип данных.|  
|[() (скобки) (выражение служб SSIS)](parentheses-ssis-expression.md)|Определяет порядок вычисления выражений.|  
|[+ (добавление) (SSIS)](add-ssis.md)|Складывает два числовых выражения.|  
|[+ (объединение) (выражение служб SSIS)](concatenate-ssis-expression.md)|Сцепляет два выражения.|  
|[+ (вычитание) (выражение служб SSIS)](subtract-ssis-expression.md)|Вычитает второе числовое выражение из первого.|  
|[+ (инверсия) (выражение служб SSIS)](negate-ssis-expression.md)|Инвертирует числовое выражение.|  
|[&#42; (умножение) (выражение служб SSIS)](multiply-ssis-expression.md)|Умножает два числовых выражения.|  
|[Деление (выражение служб SSIS)](divide-ssis-expression.md)|Делит первое числовое выражение на второе.|  
|[(Остаток от деления) (выражение служб SSIS)](modulo-ssis-expression.md)|Вычисляет целочисленный остаток после деления первого числового выражения на второе.|  
|[&#124;&#124; (логическое ИЛИ) (выражение служб SSIS)](logical-or-ssis-expression.md)|Выполняет логическую операцию ИЛИ.|  
|[&#124;&#124; (логическое И) (выражение служб SSIS)](logical-and-ssis-expression.md)|Выполняет логическую операцию И.|  
|[\! &#40;Логическое не&#41; &#40;выражение служб SSIS&#41;](logical-not-ssis-expression.md)|Инвертирует логический операнд.|  
|[&#124; (битовое включающее ИЛИ) (выражение служб SSIS)](bitwise-inclusive-or-ssis-expression.md)|Выполняет побитовую операцию ИЛИ для двух целочисленных значений.|  
|[^ (битовое исключающее ИЛИ) (выражение служб SSIS)](bitwise-exclusive-or-ssis-expression.md)|Выполняет побитовую исключающую операцию ИЛИ для двух целочисленных значений.|  
|[& (битовое И) (выражение служб SSIS)](bitwise-and-ssis-expression.md)|Выполняет побитовую операцию И для двух целочисленных значений.|  
|[~ (битовое НЕ) (выражение служб SSIS)](bitwise-not-ssis-expression.md)|Выполняет битовую инверсию целого числа.|  
|[= = (равно) (выражение служб SSIS)](equal-ssis-expression.md)|Выполняет сравнение с целью определения равенства двух выражений.|  
|[!= (не равно) (выражение служб SSIS)](unequal-ssis-expression.md)|Осуществляет операцию сравнения для определения неравенства двух выражений.|  
|[&#62; (больше чем) (выражение служб SSIS)](greater-than-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение больше второго.|  
|[&#60; (меньше чем) (выражение служб SSIS)](less-than-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение меньше второго.|  
|[&#62;= (больше или равно) (выражение служб SSIS)](greater-than-or-equal-to-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение больше второго или равно ему.|  
|[&#60;= (меньше или равно) (выражение служб SSIS)](less-than-or-equal-to-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение меньше второго или равно ему.|  
|[? : (условный) (выражение служб SSIS)](conditional-ssis-expression.md)|Возвращает одно из двух выражений на основе вычисления логического выражения.|  
  
 Сведения о размещении каждого оператора в иерархии приоритета см. в разделе [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)   
 [Примеры расширенных выражений служб Integration Services](examples-of-advanced-integration-services-expressions.md)   
 [Выражения служб Integration Services (SSIS)](integration-services-ssis-expressions.md)  
  
  
