---
title: Запрос многомерных данных с помощью многомерных Выражений | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe45a4f8fab7066ff3f606210774463f14559af7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021697"
---
# <a name="querying-multidimensional-data-with-mdx"></a>Запрос многомерных данных с помощью многомерных выражений
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|[Ключевые понятия многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)|Многомерные выражения применяются для запросов многомерных данных или для работы с кубами. Сначала необходимо ознакомиться с основными понятиями и терминами, связанными с измерениями служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)|Язык многомерных выражений позволяет обращаться с запросами к многомерным объектам (например, кубам) и возвращать многомерные наборы ячеек, содержащие данные куба. Этот раздел и его подразделы содержат общие сведения о многомерных запросах.|  
|[Основные понятия о сценариях многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)|В службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] скрипты многомерных выражений состоят из одного или нескольких многомерных выражений или инструкций, заполняющих куб вычислениями.<br /><br /> Скрипт многомерных выражений определяет процесс вычислений для куба. Скрипт многомерных выражений также считается частью самого куба. Поэтому изменение скрипта многомерных выражений, связанного с кубом, сразу изменяет процесс вычислений для куба.<br /><br /> Для создания скриптов многомерных выражений можно воспользоваться конструктором кубов в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Элементы синтаксиса многомерных Выражений & #40; Многомерные Выражения & #41;](../../../mdx/mdx-syntax-elements-mdx.md)   
 [Справочник по языку многомерных Выражений & #40; Многомерные Выражения & #41;](../../../mdx/mdx-language-reference-mdx.md)  
  
  
