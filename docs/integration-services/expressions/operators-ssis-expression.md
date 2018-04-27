---
title: Операторы (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7ecc1a2a6c19f44b3dcc43f7daf1b9bb4caf9174
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="operators-ssis-expression"></a>Операторы (выражение служб SSIS)
  В этом разделе дано описание операторов, возможность использования которых дает язык выражений, а также их приоритет и ассоциативность, используемую средством оценки выражений.  
  
 В следующей таблице содержится список разделов, посвященных операторам.  
  
|Оператор|Description|  
|--------------|-----------------|  
|[Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md)|Преобразует выражение одного типа данных в другой тип данных.|  
|[() (скобки) (выражение служб SSIS)](../../integration-services/expressions/parentheses-ssis-expression.md)|Определяет порядок вычисления выражений.|  
|[+ (добавление) (SSIS)](../../integration-services/expressions/add-ssis.md)|Складывает два числовых выражения.|  
|[+ (объединение) (выражение служб SSIS)](../../integration-services/expressions/concatenate-ssis-expression.md)|Сцепляет два выражения.|  
|[+ (вычитание) (выражение служб SSIS)](../../integration-services/expressions/subtract-ssis-expression.md)|Вычитает второе числовое выражение из первого.|  
|[+ (инверсия) (выражение служб SSIS)](../../integration-services/expressions/negate-ssis-expression.md)|Инвертирует числовое выражение.|  
|[&#42; (умножение) (выражение служб SSIS)](../../integration-services/expressions/multiply-ssis-expression.md)|Умножает два числовых выражения.|  
|[/ (деление) (выражение служб SSIS)](../../integration-services/expressions/divide-ssis-expression.md)|Делит первое числовое выражение на второе.|  
|[% (остаток от деления) (выражение служб SSIS)](../../integration-services/expressions/modulo-ssis-expression.md)|Вычисляет целочисленный остаток после деления первого числового выражения на второе.|  
|[&#124;&#124; (логическое ИЛИ) (выражение служб SSIS)](../../integration-services/expressions/logical-or-ssis-expression.md)|Выполняет логическую операцию ИЛИ.|  
|[&#124;&#124; (логическое И) (выражение служб SSIS)](../../integration-services/expressions/logical-and-ssis-expression.md)|Выполняет логическую операцию И.|  
|[\! (логическое НЕ) (выражение служб SSIS)](../../integration-services/expressions/logical-not-ssis-expression.md)|Инвертирует логический операнд.|  
|[&#124; (битовое включающее ИЛИ) (выражение служб SSIS)](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)|Выполняет побитовую операцию ИЛИ для двух целочисленных значений.|  
|[^ (битовое исключающее ИЛИ) (выражение служб SSIS)](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)|Выполняет побитовую исключающую операцию ИЛИ для двух целочисленных значений.|  
|[& (битовое И) (выражение служб SSIS)](../../integration-services/expressions/bitwise-and-ssis-expression.md)|Выполняет побитовую операцию И для двух целочисленных значений.|  
|[~ (битовое НЕ) (выражение служб SSIS)](../../integration-services/expressions/bitwise-not-ssis-expression.md)|Выполняет битовую инверсию целого числа.|  
|[= = (равно) (выражение служб SSIS)](../../integration-services/expressions/equal-ssis-expression.md)|Выполняет сравнение с целью определения равенства двух выражений.|  
|[\!= (не равно) (выражение служб SSIS)](../../integration-services/expressions/unequal-ssis-expression.md)|Осуществляет операцию сравнения для определения неравенства двух выражений.|  
|[&#62; (больше чем) (выражение служб SSIS)](../../integration-services/expressions/greater-than-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение больше второго.|  
|[&#60; (меньше чем) (выражение служб SSIS)](../../integration-services/expressions/less-than-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение меньше второго.|  
|[&#62;= (больше или равно) (выражение служб SSIS)](../../integration-services/expressions/greater-than-or-equal-to-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение больше второго или равно ему.|  
|[&#60;= (меньше или равно) (выражение служб SSIS)](../../integration-services/expressions/less-than-or-equal-to-ssis-expression.md)|Выполняет сравнение с целью определения, является ли первое выражение меньше второго или равно ему.|  
|[? : (условный) (выражение служб SSIS)](../../integration-services/expressions/conditional-ssis-expression.md)|Возвращает одно из двух выражений на основе вычисления логического выражения.|  
  
 Сведения о размещении каждого оператора в иерархии приоритета см. в разделе [Operator Precedence and Associativity](../../integration-services/expressions/operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)   
 [Примеры расширенных выражений служб Integration Services](../../integration-services/expressions/examples-of-advanced-integration-services-expressions.md)   
 [Выражения служб Integration Services (SSIS)](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
