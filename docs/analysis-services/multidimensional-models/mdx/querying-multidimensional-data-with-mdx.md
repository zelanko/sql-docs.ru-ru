---
title: "Запрос многомерных данных с помощью многомерных Выражений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: multidimensional data [Analysis Services], querying
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 301b50713aee3068caeb5fc0b1c67cce7c286cd1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="querying-multidimensional-data-with-mdx"></a>Запрос многомерных данных с помощью многомерных выражений
  Многомерные выражения — это язык запросов, предназначенный для работы с многомерными данными и их получения в службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Многомерные выражения основаны на спецификации XML для аналитики (XMLA) с некоторыми расширениями для служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Многомерные выражения состоят из идентификаторов, значений, инструкций, функций и операторов, которые службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] могут вычислять для получения объекта (например, набора или элемента) или скалярного значения (например, строки или числа).  
  
 Многомерные запросы и выражения в службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] применяются для следующих целей:  
  
-   возврат данных из куба служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] клиентскому приложению;  
  
-   форматирование результатов запроса;  
  
-   выполнение задач по конструированию кубов, в том числе для определения вычисляемых элементов, именованных наборов, назначений с указанием области и ключевых показателей эффективности;  
  
-   выполнение задач администрирования, включая защиту измерений и ячеек.  
  
 Синтаксис многомерных выражений внешне похож на синтаксис языка SQL, который обычно используется в реляционных базах данных. Тем не менее, многомерные выражения не являются расширением языка SQL и во многом от него отличаются. Для создания многомерных выражений, предназначенных для конструирования или защиты кубов, или для создания запросов многомерных выражений, возвращающих или форматирующих многомерные данные, необходимо изучить основные понятия многомерных выражений и многомерного моделирования, а также синтаксис элементов, операторов, инструкций и функций многомерных выражений.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основные понятия многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)|Многомерные выражения применяются для запросов многомерных данных или для работы с кубами. Сначала необходимо ознакомиться с основными понятиями и терминами, связанными с измерениями служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|[Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)|Язык многомерных выражений позволяет обращаться с запросами к многомерным объектам (например, кубам) и возвращать многомерные наборы ячеек, содержащие данные куба. Этот раздел и его подразделы содержат общие сведения о многомерных запросах.|  
|[Основные принципы создания скриптов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)|В службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]скрипты многомерных выражений состоят из одного или нескольких многомерных выражений или инструкций, заполняющих куб вычислениями.<br /><br /> Скрипт многомерных выражений определяет процесс вычислений для куба. Скрипт многомерных выражений также считается частью самого куба. Поэтому изменение скрипта многомерных выражений, связанного с кубом, сразу изменяет процесс вычислений для куба.<br /><br /> Для создания скриптов многомерных выражений можно воспользоваться конструктором кубов в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Синтаксические элементы в многомерных выражениях (многомерные выражения)](../../../mdx/mdx-syntax-elements-mdx.md)   
 [Справочник по языку многомерных выражений (многомерные выражения)](../../../mdx/mdx-language-reference-mdx.md)  
  
  
